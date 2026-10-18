# web-style-recipes Implementation Plan

> 2026-10-18 Dex 確認：正本放本 repo（~/web-style-recipes），`~/.claude/skills/web-style-recipes` 用 symlink 接出去（比照 ~/daydreamdex/cxo-skills）。
> 新 session 起手：讀本檔 → task.md，照 task.md 逐項做。

## Goal
讓全域 Claude Code 熟悉並能建出「實驗型互動首頁」的 10 種風格，並能產出給 Claude Design 用的 brief 卡。

## 來源與授權（必守）
- 來源：AI郵報〈【AI 工具地圖】ChatGPT、Claude 也能這樣玩！10 種 Vibe Coding 網站設計靈感〉，Joanna Chang，2026-10-14，https://www.aiposthub.com/vibe-coding-website-ideas/
- 原文**沒有授權或轉載聲明** → skill 內**不照抄原文**：特徵清單、流程、技術陷阱都用自己的結構與用語改寫；prompt 範本依同樣的特徵與流程重寫，不複製原文 prompt。每個風格檔頭註明出處。
- Dex 貼來的網址帶 `mcp_token`（閱讀憑證）：**任何檔案都不得寫入 token**，只用上面的乾淨網址。需要原文時用 WebFetch 讀乾淨網址。

## 結構
```
~/web-style-recipes/
  SKILL.md                    ← 方法＋陷阱＋風格索引（< 5k tokens）
  references/
    method.md                 ← 五段式方法（特徵清單／一句話流程／一次改一件事／prompt／陷阱）＋ brief 卡模板
    pitfalls.md               ← 共通技術陷阱（getUserMedia 需 localhost/HTTPS、file:// 時 Canvas 跨來源讀不到像素、低解析網格、prefers-reduced-motion、Pointer Events、100vh 不捲動、手機效能、權限被拒提示）
    styles/01-photo-booth.md … 10-gravity.md  ← 每個風格一檔
  tests/                      ← 實測產物（兩個 HTML＋截圖）
```
- 每個風格檔固定欄位：出處｜分類｜適合用途｜視覺特徵清單｜一句話流程｜迭代順序（先調什麼）｜技術棧｜專屬陷阱｜prompt 範本（自寫）｜Claude Design brief 卡（可直接貼）。
- 分類：相機類（01 自拍亭、05 賽博監控）／Canvas 動態場（02 熱感應、03 音檔可視化、06 萬花筒、10 重力感應）／文字（08 動態文字）／單一物件隱喻（04 白板便利貼、07 電子郵票）／敘事場景（09 像素房間）。

## SKILL.md 設計（照 agentskill-expertise 原則）
- description 寫「情境」不寫「功能」：做實驗型／互動式首頁、作品集或活動頁想要記憶點、提到其中任一風格名（自拍亭、熱像、聲紋、便利貼白板、監視器、萬花筒、郵票、動態文字、像素房間、重力）、要給 Claude Design 的視覺 brief 時。另寫「主動更新時機」：新增風格或實測發現新陷阱時。
- 主體放原則（五段式方法、一次改一件事、可讀性與減少動態優先），細節放 references，按需讀。
- 與現有 skill 分工寫明：本 skill 管「風格配方」；設計原則與評審交 impeccable／frontend-design；設計 token 交 design-system。

## 三種用法（Dex 2026-10-18 要求「一鍵選擇」）
| 用法 | 觸發 | 行為 |
|---|---|---|
| 自動載入 | 自然語言提到實驗型首頁或任一風格 | 載入對應風格檔後開工 |
| 一鍵選擇 | `/web-style-recipes`（無參數） | 用 AskUserQuestion 列出風格選單（每個附一句說明＋適合用途；超過 4 個時先選分類再選風格），選定後只問內容（品牌名、要放的素材），照配方產出單一 HTML |
| 直接指定 | `/web-style-recipes 熱感應`（參數＝風格名或編號） | 跳過選單直接開工 |
- 任一用法都可加「只要 brief」→ 只產出 Claude Design brief 卡，不寫程式。
- 「新增風格」：使用者丟來新風格的參考（文章、截圖、描述）→ 照五段格式寫成 `references/styles/NN-*.md`，並更新 SKILL.md 索引表；選單從索引表產生，不寫死。
- 不做成 10 個獨立指令：環境已有 300+ skill，多 10 筆常駐描述會增加選錯機率；一個 skill＋選單只常駐一筆。

## 與 Claude Design 協作
1. Claude Code 依本 skill 選風格、填入內容 → 產出 brief 卡（風格檔最後一節的模板）。
2. Dex 把 brief 卡貼進 Claude Design 做視覺探索、定方向。
3. Claude Code 照定案做單一 HTML → `npx serve` 本機跑 → 桌機＋手機寬度截圖 → impeccable 評一輪。

## 驗證
- 觸發：新 session 說「幫我做一個熱感應風格的首頁」「首頁想做得像白板貼便利貼」，確認 skill 被自動載入（不點名 skill）。
- 實作：產出 02 熱感應、04 白板便利貼兩個單一 HTML，`npx serve` 下桌機 1440 與手機 390 寬度截圖；減少動態效果開啟時動畫降級；白板 localStorage 重新整理後內容仍在。
- 失敗就回頭改 SKILL.md 或風格檔，再測（一次改一件事）。
