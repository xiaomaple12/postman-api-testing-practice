# Postman API Testing Project

這是一個使用 Postman、Newman 與 GitHub Actions 建立的 API 測試練習專案，主要目的是練習 QA 在 API 測試中的基本流程，包含建立 API request、檢查 response、使用 environment variables、透過 Newman 執行 Postman Collection，以及使用 GitHub Actions 建立簡易 CI 流程。

## 專案目的

本專案用來練習 API 測試流程，模擬 QA 如何透過 Postman 驗證 API 是否符合預期。

練習重點包含：

* 使用 Postman 建立 API request
* 檢查 status code 是否正確
* 檢查 response body 是否符合預期
* 檢查 headers 是否正確設定
* 使用 environment variables 管理 baseUrl 等測試環境資料
* 使用 Newman 在命令列執行 Postman Collection
* 使用 GitHub Actions 自動執行 API 測試
* 理解 API 測試如何整合到 QA / CI 流程中

## 使用工具

* Postman
* Newman
* Node.js / npm
* Git / GitHub
* GitHub Actions

## 專案結構

```text
Postman API Testing Project/
├── .github/
│   └── workflows/
├── screenshots/
├── Postman_API_Testing_Practice.postman_collection.json
├── Postman_Echo_Environment.postman_environment.json
└── README.md
```

## 資料夾與檔案說明

* `.github/`：放置 GitHub Actions workflow 設定，用來自動執行 Newman API 測試
* `screenshots/`：放置 Postman、Newman 或 GitHub Actions 執行結果截圖
* `Postman_API_Testing_Practice.postman_collection.json`：Postman API 測試 Collection
* `Postman_Echo_Environment.postman_environment.json`：Postman Environment 設定檔
* `README.md`：專案說明文件

## 測試內容

本專案主要練習 API 測試常見檢查項目：

1. 檢查 API 是否成功回應
2. 檢查 status code，例如 `200 OK` 代表請求成功
3. 檢查 response body 是否包含預期欄位
4. 檢查錯誤情境是否回傳正確錯誤訊息
5. 檢查 headers 是否正確設定
6. 使用 environment variables 讓測試更容易維護
7. 使用 Newman 一次執行整份 Postman Collection

## Environment Variables

本專案使用 Postman environment variables 管理重複使用的資料，例如：

```text
baseUrl
```

透過 environment variables，可以避免每支 API 都手動輸入完整網址，也方便日後切換不同環境，例如 development、staging 或 production。

範例：

```text
{{baseUrl}}/api/example
```

## Newman 執行方式

請先確認已安裝 Node.js / npm。

安裝 Newman：

```bash
npm install -g newman
```

執行 Postman Collection：

```bash
newman run Postman_API_Testing_Practice.postman_collection.json
```

如果要搭配 Environment 檔案執行：

```bash
newman run Postman_API_Testing_Practice.postman_collection.json -e Postman_Echo_Environment.postman_environment.json
```

## GitHub Actions / CI

本專案練習將 Newman 指令整合到 GitHub Actions 中，讓 API 測試可以在 GitHub 上自動執行。

流程概念：

```text
Postman 建立 API 測試
→ 匯出 Collection / Environment
→ Newman 用指令執行測試
→ GitHub Actions 自動執行 Newman
→ 確認 API 測試是否通過
```

這樣可以模擬 CI 流程，讓測試不只依賴手動執行，而是能在程式碼更新或排程時自動執行。

## Screenshots

`screenshots/` 資料夾中可放置 Postman 測試結果、Newman 執行結果或 GitHub Actions 成功執行的截圖，方便查看專案執行狀態與測試成果。

## 學習重點

透過這個專案，我練習了：

* API 測試基本觀念
* GET / POST / PUT / DELETE 的使用情境
* status code、response body、headers 的檢查方式
* Postman environment variables 的管理方式
* Newman 命令列執行 Postman Collection
* GitHub Actions 自動執行 API 測試
* API 測試如何整合到 QA / CI 流程中

## QA 流程對應

在 QA 流程中，Postman 可以用於 API 測試執行階段，Newman 可以讓 API 測試自動化執行，GitHub Actions 則可以將測試整合進 CI 流程。

這個專案對應到 STLC 中的：

* 測試環境準備
* 測試執行
* 自動化測試
* 回歸測試
* 測試結果確認

## 專案總結

這個專案讓我練習了從 Postman 手動建立 API 測試，到使用 Newman 命令列執行測試，再到透過 GitHub Actions 自動執行測試的流程。透過這個練習，我更理解 API 測試如何從單次手動測試，逐步延伸到可重複執行的自動化測試流程。
