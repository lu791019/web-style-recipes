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
- [ ] `ln -s ~/web-style-recipes ~/.claude/skills/web-style-recipes`；新 session 確認出現在 skill 清單

## 3. 實測
- [ ] 新 session 不點名觸發 → skill 自動載入
- [ ] `/web-style-recipes` 無參數 → 出現選單；`/web-style-recipes 熱感應` → 直接開工；加「只要 brief」→ 只出 brief 卡
- [ ] 熱感應、白板便利貼兩個 HTML；npx serve；1440／390 截圖；減少動態效果；白板 localStorage
- [ ] 依結果修 skill

## 4. 收尾
- [ ] commit；回報 Dex（截圖、觸發結果、修了什麼）
- [ ] 問 Dex 是否推到私有 GitHub repo
