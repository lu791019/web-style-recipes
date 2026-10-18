# web-style-recipes Tasks

## 0. 準備
- [x] 建 repo、implementation_plan.md、task.md（2026-10-18，Dex 確認位置／名稱／範圍）
- [ ] 載入 agentskill-expertise skill 當設計依據（已讀 SKILL.md）；WebFetch 乾淨網址重讀原文（未做：本輪用 Dex 提供的改寫素材；不得寫入 token）

## 1. 撰寫
- [x] references/method.md（五段式方法＋brief 卡模板）
- [x] references/pitfalls.md
- [x] references/styles/ 10 檔（自寫，不照抄；檔頭出處）
- [x] SKILL.md（description 情境導向、風格索引表、分工、更新時機；< 5k tokens）
- [ ] 自查：grep 原文長句確認沒有照抄（未做，需讀原文）；grep 確認沒有 mcp_token（已通過）

## 2. 接線
- [x] symlink 建好；新 session 的 skill 清單出現 web-style-recipes

## 3. 實測
- [x] 不點名觸發：熱感應、白板兩個 session 都自動載入 skill，且只讀對應風格檔＋pitfalls
- [x] `/web-style-recipes 郵票 只要 brief` → 只出 brief 卡、未寫檔
- [ ] ⏳ `/web-style-recipes` 無參數選單：需互動模式，請 Dex 手動試
- [x] 兩個 HTML（tests/thermal、tests/whiteboard）；本機伺服器＋無頭 Chrome 1440／390 截圖；兩者都有 prefers-reduced-motion 與 Pointer Events，白板有 localStorage
- [x] 依結果修 skill：熱感應「跟隨標籤撞刻度」、白板「手機便利貼裁切重疊」「手機工具列放不下」寫進專屬陷阱

## 4. 收尾
- [ ] commit；回報 Dex（截圖、觸發結果、修了什麼）
- [ ] 問 Dex 是否推到私有 GitHub repo
