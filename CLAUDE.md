# .podcast_pages — 專案層規則

> 全域行為規則見 `~/.claude/CLAUDE.md`。本檔只放本 repo 專屬的鐵則。
> 分級：`static`（純靜態內容站，只放 RSS 與節目頁，無程式碼、無金鑰）。

## 這個 repo 是什麼

四大名著與經典文學 Podcast 的 RSS 託管處，走 GitHub Pages（$0）。
Apple Podcasts 與 Spotify 直接抓這裡的 `feed.xml`，所以**它是對外表面，不是內部檔案**。

## 鐵則

- ⚠️⚠️ **本 repo 由程式產生，不要手改。** 內容的真正來源是
  `~/sasugod.tube/pipeline/podcast_sync.py`，每次影片上架後重寫 feed 再 commit。
  手改會在下一次同步被覆蓋掉，而且不會有人發現。
- ⚠️⚠️ **推不上去等於沒發佈，而 log 只印一行「不阻斷」。**
  2026-06-29 到 2026-08-27 之間，遠端整整停了兩個月：本機一路 commit，
  push 卻被 pre-push 閘門擋著（缺本檔與 `.sasugod-tier`），
  sub 上還多一層沒有憑證來源。期間每一集都只上了 YouTube，
  **播客平台一集都沒收到**，是主人問「今天的影片呢」時順著查出來的。
  真正的判準是**線上 feed 的最後一集日期**，不是「同步程式跑完沒噴錯」：
  `curl -s https://podcast.sasugod.com/story-never-end_zh/feed.xml | grep -o "<pubDate>[^<]*" | head -1`
- ⚠️ 憑證走 repo-local 的 credential helper，每次現向金鑰庫取
  `GITHUB_TOKEN_SASUGOD`，**值不落地**。不要改成把 token 寫進檔案或改 remote URL。
- ⚠️ `CNAME` 與 `.nojekyll` 不可刪：前者綁 `podcast.sasugod.com`，
  後者讓 GitHub Pages 不要用 Jekyll 處理（底線開頭的目錄會被 Jekyll 吃掉）。
