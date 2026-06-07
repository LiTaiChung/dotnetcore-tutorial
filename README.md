# .NET 9 從零開始 Slidev 教學

這是一份使用 Slidev 製作的繁體中文教學投影片，主題是用 VS Code 與 C# Dev Kit 從零開始學 .NET 9。

## 開始預覽

```bash
pnpm install
pnpm run dev
```

預設會開在 <http://localhost:3030>。

## VS Code 教學重點

- 安裝 `C# Dev Kit`
- 使用 `.NET: New Project` 建立 Console App 與 ASP.NET Core Web API
- 使用 Run and Debug 執行與中斷點除錯
- 使用 Testing 面板執行 xUnit 測試
- 對照 `dotnet` CLI 理解背後流程

## 編輯投影片

主要內容在 [slides.md](./slides.md)。

常用指令：

```bash
pnpm run dev
pnpm run build
pnpm run export
```
