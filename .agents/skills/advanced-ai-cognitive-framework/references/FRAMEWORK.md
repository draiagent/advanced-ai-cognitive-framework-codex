# 進階 AI 認知框架：12 層詳細版

## L1｜機率生成層

### 核心

語言模型根據輸入與既有參數，逐步生成可能的輸出。生成機制本身不等於查證機制。

### 常見錯誤

- 認為語句流暢代表真實
- 認為模型「記得」某一份明確資料
- 把高機率答案當成唯一正解

### 控制方法

- 要求來源
- 對重要主張建立查證步驟
- 將答案分成事實、推論與未知

---

## L2｜模式學習層

### 核心

模型從大量資料學習統計、語義與結構模式，但資料可能不完整、過時、錯誤或有偏差。

### 診斷問題

- 訓練資料是否可能缺少此領域？
- 該領域是否快速變化？
- 是否存在文化、語言或樣本偏差？
- 是否可能把相關性誤認因果？

### 控制方法

- 對時效敏感資訊使用檢索
- 優先使用領域權威資料
- 不以模型記憶取代當前證據

---

## L3｜上下文工程層

### Context Map

```text
System / Developer Instructions
        +
User Goal
        +
Conversation History
        +
Files and Data
        +
Memory
        +
Retrieved Evidence
        +
Tool Results
        =
Effective Context
```

### 失敗模式

- 缺少決策目標
- 缺少時間、地點、族群或版本
- 文件片段不完整
- 多個限制互相衝突
- 過多無關內容稀釋關鍵訊息

### 控制方法

先做 Context Audit：

```text
必要資訊：
已提供：
缺少：
衝突：
可合理假設：
必須詢問：
```

---

## L4｜提示詞工程層

提示詞不是魔法咒語，而是任務規格。

### 高品質結構

```text
Goal → Context → Inputs → Constraints → Process → Output → Evaluation
```

### 重要原則

- 明確定義完成條件
- 提供正反例
- 指定不能做什麼
- 指定資料時效與來源標準
- 將大任務拆成可驗證階段

---

## L5｜推理分解層

### 目的

把複雜問題拆解成可檢查的小問題，而不是直接跳到結論。

### 方法

- 問題樹
- 假設表
- 因果鏈
- 決策矩陣
- 情境分析
- 敏感度分析
- 反例測試

### 注意

提供可審核的推理摘要，不要求或揭露模型私密思考過程。

---

## L6｜工具使用層

### 工具角色

| 工具 | 適合任務 |
|---|---|
| Web/Search | 最新公共資訊 |
| Repository files | 專案真實狀態 |
| Python | 計算、資料處理、驗證 |
| SQL | 結構化資料查詢 |
| Browser | 網頁操作與流程驗證 |
| MCP/API | 外部系統與企業資料 |
| Tests/Linters | 軟體行為驗證 |

### 原則

模型負責協調，工具提供外部狀態。工具輸出仍要檢查來源、時間與錯誤。

---

## L7｜記憶管理層

### 可保留

- 長期偏好
- 穩定角色
- 長期專案名稱
- 固定格式與工作習慣

### 不應混入長期記憶

- 一次性密碼
- 短期狀態
- 未確認推測
- 不必要的敏感資訊

### 核心問題

> 這項資訊未來仍有效嗎？保存它會改善後續任務嗎？

---

## L8｜知識檢索層

### RAG 基本流程

```text
Query
→ Retrieval
→ Ranking
→ Context Assembly
→ Generation
→ Citation
→ Verification
```

### 失敗模式

- 找到內容相似但不支持主張的文件
- 文件已過期
- 只檢索到單一觀點
- 引用段落與結論不一致
- 檢索結果被模型過度延伸

---

## L9｜多代理協作層

### 建議角色

- Researcher：蒐集證據
- Analyst：建立分析
- Skeptic：尋找反例
- Verifier：核對主張與來源
- Editor：整合與表達
- Governor：檢查風險與合規

### 使用條件

多代理不是越多越好。適用於：

- 可平行拆分
- 高複雜度
- 需要獨立批判
- 單一路徑偏誤成本高

---

## L10｜人機共智層

### 人類應保留

- 價值判斷
- 利害關係取捨
- 法律與倫理責任
- 最終高風險決策
- 組織政治與情境理解
- 對人的同理與溝通責任

### AI 適合

- 蒐集
- 整理
- 比較
- 模擬
- 草擬
- 自動化
- 提醒

---

## L11｜AI 治理層

### 六項治理面向

1. 正確性
2. 隱私
3. 資安
4. 法規
5. 偏差與公平
6. 稽核與責任

### Governance Record

```text
Use case:
Data used:
Model/tool:
Known limitations:
Human owner:
Approval point:
Retention rule:
Incident process:
```

---

## L12｜AI 作業系統層

### 成熟架構

```text
Business Goal
    ↓
Task Specification
    ↓
Context + Memory + Retrieval
    ↓
Reasoning + Tools + Agents
    ↓
Verification + Governance
    ↓
Human Decision
    ↓
Execution
    ↓
Measurement and Learning
```

### 成熟度

| 階段 | 特徵 |
|---|---|
| 1. 個人試用 | 零散聊天 |
| 2. 提示詞標準化 | 有模板 |
| 3. 工作流 | 可重複步驟 |
| 4. Agent 化 | 工具與自動化 |
| 5. 治理化 | 權限、稽核、責任 |
| 6. AI 原生 | 以 AI 重設流程與商模 |
