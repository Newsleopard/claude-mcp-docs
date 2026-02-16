> [English](.)

# 電子豹 × Claude AI — 連接設定指南

將你的電子豹帳號連接到 Claude AI，就能用自然語言管理 EDM 活動、查看報表、分析成效。不需要寫程式，直接用中文對話就能操作。

---

## 什麼是 MCP 整合？

MCP（Model Context Protocol）是 Anthropic 推出的開放協定，讓 Claude AI 能夠直接存取外部服務。

連接電子豹之後，你可以在 Claude 的對話中直接：

- 查看最近 EDM 活動的開信率、點擊率
- 建立新的電子報活動
- 分析活動成效並取得 AI 優化建議
- 比較多次活動表現
- 管理名單群組、查詢帳戶額度

所有操作都透過你的電子豹帳號授權，Claude 不會儲存你的對話內容。

---

## 事前準備

- **Claude 方案**：需要 Claude Pro、Max、Team 或 Enterprise 方案（免費版不支援）
- **電子豹帳號**：任何方案皆可使用

---

## 設定方式

### Claude.ai（網頁版）— 推薦

這是最簡單的連接方式，完全不需要安裝任何軟體。

1. 前往 [Claude.ai](https://claude.ai) 並登入
2. 點擊左下角的**頭像** → **Settings**（設定） → **Connectors**
3. 捲到最下方，點擊 **Add custom connector**
4. 在 URL 欄位輸入：

   ```text
   https://mcp.newsleopard.com/sse
   ```

5. 點擊 **Add** — 會跳轉到電子豹登入頁面
6. 輸入你的電子豹帳號密碼，點擊**允許**授權
7. 回到 Claude.ai，連接器顯示為 **Connected**

連接完成後：

- 你可以在 Connectors 設定中開關個別功能
- 連接器會自動同步到 Claude iOS 和 Android App
- 手機端不需要額外設定

### Claude Desktop（桌面版）

#### 方法一：Connectors UI（推薦）

操作方式與網頁版相同：

1. 開啟 Claude Desktop → 點擊**頭像** → **Settings** → **Connectors**
2. 點擊 **Add custom connector**
3. 輸入 URL：

   ```text
   https://mcp.newsleopard.com/sse
   ```

4. 點擊 **Add** — 瀏覽器會自動開啟登入頁面
5. 輸入電子豹帳號密碼並授權
6. 回到 Claude Desktop 即可使用

透過 Connectors UI 新增的連接器會同步到 Claude.ai 和手機 App。

#### 方法二：mcp-remote + API Key（進階）

如果你偏好使用 API Key 認證，需要先安裝 [Node.js](https://nodejs.org/)。

設定檔位置：

- **macOS：** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows：** `%APPDATA%\Claude\claude_desktop_config.json`

將以下內容加入設定檔：

```json
{
  "mcpServers": {
    "newsleopard": {
      "command": "npx",
      "args": [
        "mcp-remote@latest",
        "https://mcp.newsleopard.com/sse",
        "--header",
        "x-api-key: ${NEWSLEOPARD_API_KEY}"
      ],
      "env": {
        "NEWSLEOPARD_API_KEY": "你的 API Key"
      }
    }
  }
}
```

API Key 取得方式：登入電子豹 → **設定** → **API 設定** → **產生新的 API Key**。

儲存後完全關閉並重新開啟 Claude Desktop，聊天輸入框應該會出現 MCP 伺服器圖示。

### Claude Code（CLI）

在終端機執行以下指令：

```bash
claude mcp add newsleopard --transport http https://mcp.newsleopard.com/mcp
```

首次使用時會自動跳出 OAuth 授權流程。

### Cursor

1. 開啟 **Settings** → **MCP** → **New MCP Server**
2. 填入以下資訊：

```yaml
Name: NewsLeopard
URL: https://mcp.newsleopard.com/mcp
Headers:
  x-api-key: 你的 API Key
```

API Key 請從電子豹後台的 **設定** → **API 設定** 取得。

---

## 你可以做什麼？

連接完成後，直接在 Claude 對話中用中文下指令即可。以下是幾個常見的使用範例：

### 查看活動表現

```text
顯示我最近的 EDM 活動表現
```

Claude 會列出最近 10 次活動的名稱、寄送日期、收件人數、開信率、點擊率、退信率、退訂數，幫你快速掌握整體表現。

### 建立新活動

```text
幫我建立一封新的電子報，寄給 VIP 客戶，主題是春季特賣
```

Claude 會先確認可用的寄件人地址和名單群組，然後開啟互動式表單讓你填寫活動細節（寄件人、收件群組、主旨、內容）。

### 分析活動成效

```text
分析上一次活動的成效，給我優化建議
```

Claude 會取得最新活動的詳細數據，進行深度分析（對比業界平均、評估點擊率、退信率），並給出具體的優化建議，包括主旨行改善、最佳寄送時間、內容優化、名單清理等。

### 比較多次活動

```text
比較最近 3 次活動的表現
```

Claude 會產生並排比較表，顯示各項指標的差異、趨勢變化，並指出哪次活動表現最好及原因。

### 查詢帳戶額度與最佳寄送時間

```text
我這個月還能寄多少封信？最佳寄送時間是什麼時候？
```

Claude 會查詢你的帳戶餘額和寄送額度，同時根據歷史開信數據推薦最佳寄送時段。

---

## 可用功能一覽

### 活動管理

- 建立新的 EDM 活動（含互動式表單）
- 編輯活動內容（文字修改、區塊替換、完整 HTML）
- 暫停進行中的活動
- 寄送前預檢（驗證寄件人、名單、內容是否就緒）

### 報表分析

- 查看活動成效指標（開信率、點擊率、退信率）
- AI 深度分析，附帶優化建議
- 多活動並排比較
- 每個連結的點擊明細
- GA4 電商營收數據
- 匯出每位收件人的詳細 CSV 報表

### 名單管理

- 查看所有名單群組與訂閱人數
- 建立新的名單群組
- 依開信率排名的群組清單

### 範本與自動化

- 瀏覽官方範本和自訂範本
- 儲存新範本供日後使用
- 啟動或停止自動化流程

### 帳戶管理

- 查詢寄送額度與帳戶餘額
- 查看已驗證的寄件人地址
- 取得基於歷史數據的最佳寄送時間建議

---

## 常見問題

### Claude.ai 沒有看到 Connectors 選項

Custom Connectors 需要 Claude Pro、Max、Team 或 Enterprise 方案。免費版不支援此功能。

### 連接時出現 401 錯誤

- **Claude.ai / Claude Desktop Connectors**：請確認已完成登入並點擊「允許」授權。
- **使用 API Key**：請確認 API Key 正確且未過期。可到電子豹後台重新產生。

### Claude Desktop 看不到電子豹工具

1. 確認設定檔的 JSON 語法正確
2. 確認已安裝 Node.js
3. 完全關閉 Claude Desktop 後重新開啟
4. 檢查 log 檔：
   - macOS：`~/Library/Logs/Claude/mcp*.log`
   - Windows：`%APPDATA%\Claude\logs\mcp*.log`

### 回應速度比較慢

MCP 伺服器透過網路連接電子豹 API。第一次請求可能需要 2-3 秒（伺服器暖機），後續請求會比較快。

---

## 隱私權與資料安全

- 僅傳送操作所需的最少資料（如活動 ID、名單 ID）
- **不儲存任何對話內容**
- 全程使用 HTTPS 加密傳輸（TLS 1.2+）
- 隱私權政策：<https://www.newsleopard.com/legal/privacy-policy/>

---

## 需要協助？

- **客服信箱：** <service@newsleopard.tw>
- **電子豹官網：** <https://www.newsleopard.com>
- **API 文件：** <https://newsleopard.com/api/v1/>
