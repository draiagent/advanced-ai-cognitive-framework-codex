# Advanced AI Cognitive Framework for Codex

> 將「AI 為什麼會出錯」升級為可在 Codex 重複執行的進階 AI 認知、查證、推理與治理框架。

## 專案定位

本專案不是一般提示詞集合，而是一套可被 Codex 載入與執行的 **Agent Skill**。  
它協助使用者在分析、研究、企劃、教學、內容生成與企業決策時，降低以下風險：

- 把語言流暢誤認為事實正確
- 把模型推測誤認為已驗證知識
- 忽略資料時效、來源與適用範圍
- 因上下文不足產生幻覺
- 使用模糊提示詞導致錯誤方向
- 缺乏風險分級與人工覆核
- 只生成答案，沒有建立驗證閉環

---

## 核心架構：12 層 AI 認知模型

| 層級 | 模組 | 核心問題 | 主要產出 |
|---|---|---|---|
| L1 | 機率生成 | AI 如何形成文字？ | 區分預測與查證 |
| L2 | 模式學習 | AI 從何而來？ | 訓練資料限制盤點 |
| L3 | 上下文工程 | AI 現在看見什麼？ | Context Map |
| L4 | 提示詞工程 | 如何降低歧義？ | 結構化任務規格 |
| L5 | 推理分解 | 問題如何拆解？ | 假設、步驟與依賴 |
| L6 | 工具使用 | 哪些部分必須外部查證？ | 搜尋、程式、資料工具計畫 |
| L7 | 記憶管理 | 哪些資訊應保留？ | 穩定偏好與專案脈絡 |
| L8 | 知識檢索 | 如何取得新資料？ | RAG／搜尋／文件證據 |
| L9 | 多代理協作 | 如何避免單一路徑偏誤？ | 研究、批判、驗證分工 |
| L10 | 人機共智 | 人應保留什麼決策權？ | 人工判斷點 |
| L11 | AI 治理 | 如何確保安全、合法、可追溯？ | 風險與稽核紀錄 |
| L12 | AI 作業系統 | 如何制度化？ | 可重複工作流與品質閘門 |

---

## GitHub 結構

```text
advanced-ai-cognitive-framework-codex/
├── README.md
├── AGENTS.md
├── CONTRIBUTING.md
├── LICENSE
├── examples/
│   └── USAGE.md
└── .agents/
    └── skills/
        └── advanced-ai-cognitive-framework/
            ├── SKILL.md
            └── references/
                ├── FRAMEWORK.md
                ├── RELIABILITY_PROTOCOL.md
                └── OUTPUT_TEMPLATES.md
```

---

## 安裝方式

### 方法一：直接放入專案

將整個資料夾加入 Git 儲存庫。Codex 會從儲存庫中的：

```text
.agents/skills/advanced-ai-cognitive-framework/SKILL.md
```

辨識此技能。

### 方法二：只安裝技能

將以下資料夾複製到其他專案：

```text
.agents/skills/advanced-ai-cognitive-framework/
```

### 方法三：個人全域技能

可將技能資料夾放入：

```text
$HOME/.agents/skills/advanced-ai-cognitive-framework/
```

---

## 使用方式

在 Codex 中輸入：

```text
$advanced-ai-cognitive-framework
請分析這份企業 AI 導入計畫，找出事實、推論、假設、風險與需要查證的部分。
```

或直接描述符合此技能範圍的任務，讓 Codex 自動判斷是否啟用。

### 常見任務

```text
$advanced-ai-cognitive-framework
將這篇 AI 文章改寫為大學課程教材，先檢查概念是否過度簡化。
```

```text
$advanced-ai-cognitive-framework
評估這份市場研究報告，禁止把推測寫成事實，並列出證據缺口。
```

```text
$advanced-ai-cognitive-framework
建立一個可驗證的分析流程：先分解問題，再搜尋資料，再交叉驗證，最後輸出信心等級。
```

---

## 標準輸出結構

技能預設產生八個區塊：

1. **任務定義**
2. **已知事實**
3. **推論與假設**
4. **資訊缺口**
5. **查證計畫**
6. **分析與建議**
7. **風險、限制與信心等級**
8. **下一個最佳行動**

---

## 品質原則

### 1. 先區分，再回答

所有重要陳述分成：

- `FACT`：有證據支持
- `INFERENCE`：由證據推導
- `ASSUMPTION`：目前未驗證
- `UNKNOWN`：資訊不足
- `OPINION`：主觀判斷
- `RECOMMENDATION`：基於目標的建議

### 2. 高風險任務提高驗證門檻

醫療、法律、金融、資安、法規、公共政策與重大商業決策，必須：

- 使用最新資料
- 優先採用第一手或權威來源
- 至少進行雙來源交叉驗證
- 明示不確定性
- 保留人工決策權

### 3. 不把自我檢查當成外部證據

模型重新閱讀自己的答案，只是內部一致性檢查，不等於事實查證。

### 4. 產出必須可追溯

重要結論應能追溯到：

```text
結論 → 證據 → 來源 → 日期 → 適用範圍
```

---

## Codex 設計原則

本專案採用：

- **短版 `AGENTS.md`**：只放儲存庫級工作規則
- **完整 `SKILL.md`**：定義技能啟用條件與主要流程
- **references/**：承載長篇框架與模板
- **漸進式揭露**：僅在需要時讀取詳細文件
- **驗收條件**：每次任務都要定義完成標準

---

## 官方參考

- Codex Skills: https://developers.openai.com/codex/skills
- AGENTS.md: https://developers.openai.com/codex/guides/agents-md
- Codex Best Practices: https://developers.openai.com/codex/learn/best-practices

---

## 版本

**v2.0.0 — Advanced Codex Edition**

適用於：

- AI 講師課程設計
- 企業 AI 導入
- 研究與報告查證
- 內容生成與審稿
- Agentic Workflow
- GitHub／Codex 知識型專案
