# CHANGELOG

本檔記錄的是**這個 repo 的結構變更**，不是每天的節目更新。
節目更新看 commit 紀錄（`feeds update <日期>`）與線上 feed 本身。

## [1.0.0] - 2026-08-27

### 修正
- 補上 `.sasugod-tier`（`static`）、`CLAUDE.md`、`VERSION`、本檔。
  缺這幾個檔會被 pre-push 規範閘門擋下，而**擋下的訊息只印在產線 log 的
  「Podcast 同步失敗（不阻斷）」那一行**，沒有任何出口通到主人。
  結果是遠端從 2026-06-29 起整整兩個月沒有更新，
  Apple 與 Spotify 上的最後一集停在 2026-07-29，
  期間累積 10 個未推的 commit。本次一併推上。
