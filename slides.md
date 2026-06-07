---
theme: light-icons
colorSchema: light
layout: image-header-intro
imageHeader: /dotnet9-header.svg
imageRight: /illustrations/dotnet-hero.svg
title: .NET 9 從零開始
info: |
  ## .NET 9 從零開始

  使用 VS Code、C# Dev Kit 與 .NET SDK 建立 Console、Web API、測試與發佈流程。
drawings:
  persist: false
transition: slide-left
comark: true
lineNumbers: true
duration: 90min
fonts:
  sans: Noto Sans TC
  serif: Noto Serif TC
  mono: JetBrains Mono
---

<div class="leading-snug text-black dark:text-white text-opacity-60 dark:text-opacity-60 mt-4 text-2xl">
  使用 VS Code Extension 學會 C#、專案、API、Debug、測試與發佈
</div>

<div class="mt-6 text-lg text-black dark:text-white text-opacity-50 dark:text-opacity-50">
  適合第一次接觸 .NET / C# 的後端入門課
</div>

<div class="cover-illo">
  <div class="cover-illo-card main">
    <light-icon icon="device-laptop" size="78px" color="#0e9f9a" />
  </div>
  <div class="cover-illo-card side">
    <light-icon icon="server" size="48px" color="#f3b33d" />
  </div>
  <div class="cover-illo-card badge">
    <light-icon icon="code" size="20px" />
    .NET 9 Workshop
  </div>
  <div class="cover-illo-line one"></div>
  <div class="cover-illo-line two"></div>
</div>

<!--
開場：這堂課假設大家會基本電腦操作，但不假設會 C# 或 .NET。
目標是讓學生能自己在 VS Code 裡建立、執行、Debug 一個 API。
-->

---
layout: dynamic-image
left: false
image: /illustrations/learning-map.svg
---

# 今天會學到什麼

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="list-check" /></div>
  <div class="icon-secondary"><light-icon icon="target" /></div>
  <div class="icon-tertiary"><light-icon icon="rocket" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

<v-clicks>

- .NET、C#、ASP.NET Core 之間的關係
- 用 VS Code 安裝 C# Dev Kit 與 .NET SDK
- 建立第一個 Console App
- 看懂專案檔、Program.cs 與 dotnet CLI
- 建立 Minimal API，使用 Swagger / OpenAPI 測試
- 用 VS Code 下中斷點 Debug
- 加入 NuGet 套件、設定檔、相依性注入
- 寫第一個測試，最後發佈成可部署檔案

</v-clicks>

---
layout: dynamic-image
left: false
image: /illustrations/learning-map.svg
---

# 先釐清名字

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="braces" /></div>
  <div class="icon-secondary"><light-icon icon="stack" /></div>
  <div class="icon-tertiary"><light-icon icon="sitemap" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```mermaid
%%{init: {"theme": "base", "themeVariables": {"fontFamily": "Noto Sans TC, Inter, sans-serif", "primaryColor": "#e8fbf8", "primaryTextColor": "#123b4a", "primaryBorderColor": "#0e9f9a", "lineColor": "#80cbc4", "secondaryColor": "#fff8e1", "tertiaryColor": "#f6fffe", "clusterBkg": "#f6fffe", "clusterBorder": "#8bd8d1"}}}%%
flowchart LR
  A["C#"] --> B[".NET Runtime"]
  C[".NET SDK"] --> D["Build / Run / Test / Publish"]
  B --> E["Console App"]
  B --> F["ASP.NET Core API"]
  B --> G["Worker Service"]

  classDef language fill:#fff8e1,stroke:#f3b33d,color:#123b4a,stroke-width:2px;
  classDef platform fill:#e8fbf8,stroke:#0e9f9a,color:#123b4a,stroke-width:2px;
  classDef output fill:#f6fffe,stroke:#8bd8d1,color:#123b4a,stroke-width:2px;
  class A,C language;
  class B,D platform;
  class E,F,G output;
```

<div class="mt-4 grid grid-cols-3 gap-4 text-left text-sm">
  <div class="rounded border border-gray-300/30 p-4">
    <div class="font-bold">C#</div>
    <div class="opacity-75">程式語言</div>
  </div>
  <div class="rounded border border-gray-300/30 p-4">
    <div class="font-bold">.NET 9</div>
    <div class="opacity-75">執行平台與標準函式庫</div>
  </div>
  <div class="rounded border border-gray-300/30 p-4">
    <div class="font-bold">ASP.NET Core</div>
    <div class="opacity-75">建立 Web / API 的框架</div>
  </div>
</div>

<!--
.NET Core 是舊稱脈絡，現在官方主要稱 .NET。很多人仍會說 dotnet core，所以這堂課用 .NET 9 / .NET Core 9 對齊常見說法。
-->

---
layout: dynamic-image
left: false
image: /illustrations/tools-setup.svg
---

# 開發環境

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="device-desktop" /></div>
  <div class="icon-secondary"><light-icon icon="tools" /></div>
  <div class="icon-tertiary"><light-icon icon="settings" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

<div class="env-grid grid grid-cols-2 gap-5 text-sm">
<div>

### 必裝

- Visual Studio Code
- .NET 9 SDK
- VS Code Extension: C# Dev Kit

<div class="env-divider"></div>

### 建議安裝

- .NET Install Tool
- NuGet Package Manager
- REST Client 或 Thunder Client

</div>
<div>

### 檢查指令

```bash
dotnet --version
dotnet --info
code --version
```

<div class="env-divider"></div>

### 版本概念

- SDK: 建立與編譯專案
- Runtime: 執行已編譯的 App
- Target Framework: 專案目標，例如 `net9.0`

</div>
</div>

---
layout: dynamic-image
left: false
image: /illustrations/tools-setup.svg
---

# VS Code 裝 Extension

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="plug" /></div>
  <div class="icon-secondary"><light-icon icon="search" /></div>
  <div class="icon-tertiary"><light-icon icon="checkbox" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

1. 開啟 VS Code
2. 左側 Extensions
3. 搜尋並安裝 `.NET Core EditorConfig Generator`
4. 搜尋並安裝 `.NET Core Extension Pack`
5. 重新載入 VS Code

<div class="mt-8">

```txt
.NET Core EditorConfig Generator 可快速產生 C# 專案用的 .editorconfig。
.NET Core Extension Pack 會一次補齊常用的 .NET 開發工具。
```

</div>

<div class="mt-6 text-sm opacity-70">
課堂中會用 Extension 操作，也會保留 CLI 指令，方便你理解背後發生什麼事。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/code-console.svg
---

# 建立第一個專案

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="folder-plus" /></div>
  <div class="icon-secondary"><light-icon icon="terminal" /></div>
  <div class="icon-tertiary"><light-icon icon="caret-right" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

## VS Code 操作

<v-clicks>

- Command Palette: `Ctrl/Cmd + Shift + P`
- 執行 `.NET: New Project`
- 選 `Console App`
- 選資料夾並命名 `HelloDotnet`
- 按 VS Code 的 Run / Debug 執行

</v-clicks>

## 對應 CLI

```bash
dotnet new console -n HelloDotnet
cd HelloDotnet
dotnet run
```

---
layout: dynamic-image
left: false
image: /illustrations/code-console.svg
---

# Console App 長什麼樣

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="terminal-2" /></div>
  <div class="icon-secondary"><light-icon icon="code" /></div>
  <div class="icon-tertiary"><light-icon icon="message" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```csharp [Program.cs]
Console.WriteLine("Hello, .NET 9!");
```

<div class="mt-8 grid grid-cols-2 gap-6 text-left">
  <div>
    <h3>Top-level statements</h3>
    <p class="text-sm opacity-75">C# 可以省略傳統 Main 方法，讓入門程式更短。</p>
  </div>
  <div>
    <h3>執行流程</h3>
    <p class="text-sm opacity-75">編譯後由 .NET Runtime 執行，輸出到終端機。</p>
  </div>
</div>

---
layout: dynamic-image
left: false
image: /illustrations/code-console.svg
---

# 專案檔 csproj

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="file-code" /></div>
  <div class="icon-secondary"><light-icon icon="settings" /></div>
  <div class="icon-tertiary"><light-icon icon="shield-check" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```xml [HelloDotnet.csproj]
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net9.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>
</Project>
```

<v-clicks>

- `Sdk` 決定專案類型與建置能力
- `TargetFramework` 指定目標版本
- `ImplicitUsings` 自動引用常用命名空間
- `Nullable` 幫你提早發現 null 風險

</v-clicks>

---
layout: dynamic-image
left: false
image: /illustrations/code-console.svg
---

# C# 基礎語法

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="brackets" /></div>
  <div class="icon-secondary"><light-icon icon="route" /></div>
  <div class="icon-tertiary"><light-icon icon="checks" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```csharp {all|1-3|5-8|10-13|all}
string name = "Ada";
int age = 28;
bool isDeveloper = true;

if (age >= 18)
{
    Console.WriteLine($"{name} 可以建立 .NET 專案");
}

for (int i = 1; i <= 3; i++)
{
    Console.WriteLine($"第 {i} 次練習");
}
```

<div class="mt-6 text-sm opacity-75">
先學會變數、條件、迴圈，再進到物件、API 與資料庫。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/code-console.svg
---

# 方法與型別

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="math" /></div>
  <div class="icon-secondary"><light-icon icon="box" /></div>
  <div class="icon-tertiary"><light-icon icon="calculator" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```csharp {all|1-4|6-7|9-12|all}
static decimal AddTax(decimal price, decimal taxRate)
{
    return price * (1 + taxRate);
}

var total = AddTax(100m, 0.05m);
Console.WriteLine(total);

public record Product(
    int Id,
    string Name,
    decimal Price);
```

<v-clicks>

- 方法負責封裝一段可重複使用的邏輯
- `record` 適合表示資料
- 型別讓 IDE 和編譯器提早抓錯

</v-clicks>

---
layout: dynamic-image
left: false
image: /illustrations/code-console.svg
---

# dotnet CLI 心智模型

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="terminal" /></div>
  <div class="icon-secondary"><light-icon icon="git-branch" /></div>
  <div class="icon-tertiary"><light-icon icon="rocket" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```bash
dotnet new console -n Demo
dotnet restore
dotnet build
dotnet run
dotnet test
dotnet publish
```

```mermaid
%%{init: {"theme": "base", "themeVariables": {"fontFamily": "Noto Sans TC, Inter, sans-serif", "primaryColor": "#e8fbf8", "primaryTextColor": "#123b4a", "primaryBorderColor": "#0e9f9a", "lineColor": "#80cbc4", "secondaryColor": "#fff8e1", "tertiaryColor": "#f6fffe"}}}%%
flowchart LR
  A["dotnet new"] --> B["restore"]
  B --> C["build"]
  C --> D["run"]
  C --> E["test"]
  C --> F["publish"]

  classDef start fill:#fff8e1,stroke:#f3b33d,color:#123b4a,stroke-width:2px;
  classDef step fill:#e8fbf8,stroke:#0e9f9a,color:#123b4a,stroke-width:2px;
  classDef finish fill:#f6fffe,stroke:#135483,color:#123b4a,stroke-width:2px;
  class A start;
  class B,C,D,E step;
  class F finish;
  linkStyle 0,1,2,3,4 stroke:#0e9f9a,stroke-width:3px;
```

<div class="mt-4 text-sm opacity-75">
VS Code extension 很方便，但 CLI 是跨平台、自動化與 CI/CD 的共同語言。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# 建立 Web API

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="server" /></div>
  <div class="icon-secondary"><light-icon icon="browser" /></div>
  <div class="icon-tertiary"><light-icon icon="world" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

<div class="mt-6 text-3xl text-black dark:text-white text-opacity-55 dark:text-opacity-60">
  從會印字，到會回應 HTTP Request
  <light-icon icon="server" size="32px" />
</div>

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# Web API 專案

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="layout-navbar" /></div>
  <div class="icon-secondary"><light-icon icon="server" /></div>
  <div class="icon-tertiary"><light-icon icon="caret-right" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

## VS Code 操作

- Command Palette: `.NET: New Project`
- 選 `ASP.NET Core Web API`
- 命名 `TodoApi`
- 在 Solution Explorer 按 Run / Debug

## 對應 CLI

```bash
dotnet new webapi -n TodoApi
cd TodoApi
dotnet run
```

<div class="mt-6 text-sm opacity-75">
第一次執行 HTTPS 專案時，可能需要信任開發憑證。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# Minimal API

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="route" /></div>
  <div class="icon-secondary"><light-icon icon="code" /></div>
  <div class="icon-tertiary"><light-icon icon="bolt" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```csharp [Program.cs] {all|1-2|4|6|8-9|11|all}
var builder = WebApplication.CreateBuilder(args);
builder.Services.AddOpenApi();

var app = builder.Build();

app.MapOpenApi();

app.MapGet("/", () => "Hello API");
app.MapGet("/time", () => DateTimeOffset.Now);

app.Run();
```

<v-clicks>

- `builder` 設定服務與組態
- `app` 定義 middleware 與 endpoints
- `MapGet` 代表 HTTP GET 路由

</v-clicks>

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# HTTP 與路由

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="send" /></div>
  <div class="icon-secondary"><light-icon icon="router" /></div>
  <div class="icon-tertiary"><light-icon icon="database" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```mermaid
%%{init: {"theme": "base", "sequence": {"mirrorActors": false, "showSequenceNumbers": true}, "themeVariables": {"fontFamily": "Noto Sans TC, Inter, sans-serif", "actorBkg": "#e8fbf8", "actorBorder": "#0e9f9a", "actorTextColor": "#123b4a", "activationBkgColor": "#fff8e1", "activationBorderColor": "#f3b33d", "signalColor": "#0e9f9a", "signalTextColor": "#123b4a", "noteBkgColor": "#f6fffe", "noteBorderColor": "#8bd8d1"}}}%%
sequenceDiagram
  autonumber
  participant Client as Client
  participant API as ASP.NET Core API
  Client->>+API: GET /todos/1
  API-->>-Client: 200 OK + JSON
```

| 動詞 | 常見用途 | 範例 |
| --- | --- | --- |
| GET | 讀取資料 | `/todos` |
| POST | 新增資料 | `/todos` |
| PUT | 整筆更新 | `/todos/1` |
| DELETE | 刪除資料 | `/todos/1` |

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# 建立 Todo Endpoint

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="clipboard-list" /></div>
  <div class="icon-secondary"><light-icon icon="circle-plus" /></div>
  <div class="icon-tertiary"><light-icon icon="circle-check" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```csharp {all|1|3|5-10|12-13|all}
var todos = new List<TodoItem>();

app.MapGet("/todos", () => todos);

app.MapPost("/todos", (CreateTodoRequest request) =>
{
    var todo = new TodoItem(todos.Count + 1, request.Title, false);
    todos.Add(todo);
    return Results.Created($"/todos/{todo.Id}", todo);
});

public record TodoItem(int Id, string Title, bool IsDone);
public record CreateTodoRequest(string Title);
```

<div class="mt-6 text-sm opacity-75">
這是記憶體版本，重開程式資料會消失；之後再接資料庫。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# 用 OpenAPI 測試

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="file-text" /></div>
  <div class="icon-secondary"><light-icon icon="browser" /></div>
  <div class="icon-tertiary"><light-icon icon="checks" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

`.NET 9` 的 ASP.NET Core 可內建產生 OpenAPI 文件。

```csharp
builder.Services.AddOpenApi();

if (app.Environment.IsDevelopment())
{
    app.MapOpenApi();
}
```

<v-clicks>

- 開啟 `http://localhost:{port}/openapi/v1.json`
- 可搭配 Swagger UI、Scalar 或 REST Client 測試
- API 文件讓前後端更容易對齊

</v-clicks>

---
layout: dynamic-image
left: false
image: /illustrations/code-console.svg
---

# VS Code Debug

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="bug" /></div>
  <div class="icon-secondary"><light-icon icon="crosshair" /></div>
  <div class="icon-tertiary"><light-icon icon="activity" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

1. 在 `Program.cs` 左側點一下，加入 breakpoint
2. 開啟 Run and Debug
3. 選擇專案或 `.NET Core Launch`
4. 按 Start Debugging
5. 發送 request，觀察變數與呼叫堆疊

```csharp [Program.cs] {all|3|4|5|all}
app.MapPost("/todos", (CreateTodoRequest request) =>
{
    var todo = new TodoItem(todos.Count + 1, request.Title, false);
    todos.Add(todo);
    return Results.Created($"/todos/{todo.Id}", todo);
});
```

---
layout: dynamic-image
left: false
image: /illustrations/tools-setup.svg
---

# appsettings.json

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="file-text" /></div>
  <div class="icon-secondary"><light-icon icon="adjustments-horizontal" /></div>
  <div class="icon-tertiary"><light-icon icon="lock" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```json [appsettings.Development.json]
{
  "AppOptions": {
    "DefaultPageSize": 20
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}
```

<div class="mt-6 text-sm opacity-75">
設定檔放環境差異；程式碼放商業邏輯。密碼與 token 不要直接提交到 git。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# 什麼是相依性注入 DI

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="plug" /></div>
  <div class="icon-secondary"><light-icon icon="sitemap" /></div>
  <div class="icon-tertiary"><light-icon icon="box" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

<div class="grid grid-cols-2 gap-5 text-sm">
  <div class="rounded border border-gray-300/30 p-4">
    <h3>官方定義</h3>
    <p class="opacity-75">ASP.NET Core 支援 DI 設計模式，用來在類別與相依性之間達成控制權反轉。</p>
  </div>
  <div class="rounded border border-gray-300/30 p-4">
    <h3>相依物件</h3>
    <p class="opacity-75">一個物件需要另一個物件才能工作時，後者就是它的相依性。</p>
  </div>
</div>

<div class="mt-5 grid grid-cols-2 gap-5 text-sm">
  <div class="rounded border border-gray-300/30 p-4">
    <h3>直接 new 的問題</h3>
    <ul>
      <li>替換實作要修改使用類別</li>
      <li>相依性的設定散落各處</li>
      <li>單元測試變困難</li>
    </ul>
  </div>
  <div class="rounded border border-gray-300/30 p-4">
    <h3>DI 的做法</h3>
    <ul>
      <li>用介面或基底類別抽象化</li>
      <li>把服務註冊到 DI 容器</li>
      <li>由框架建立、注入和處置服務</li>
    </ul>
  </div>
</div>

---
layout: dynamic-image
left: false
image: /illustrations/web-api.svg
---

# DI 在 ASP.NET Core 裡怎麼用

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="plug" /></div>
  <div class="icon-secondary"><light-icon icon="sitemap" /></div>
  <div class="icon-tertiary"><light-icon icon="box" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```csharp {all|1|3-7|9|all}
builder.Services.AddScoped<IMyDependency, MyDependency>();

public class MyService(IMyDependency dependency)
{
    public void WriteMessage() =>
        dependency.WriteMessage("Service is resolved");
}

builder.Services.AddSingleton<MyCache>();
```

<v-clicks>

- 服務通常在 `Program.cs` 透過 `builder.Services` 註冊
- 容器解析相依性圖形，回傳完整建立好的服務
- `AddScoped` 常用於 request 範圍的服務
- `AddSingleton` 建立後會重複使用同一個實例

</v-clicks>

---
layout: dynamic-image
left: false
image: /illustrations/testing-publish.svg
---

# 加 NuGet 套件

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="package" /></div>
  <div class="icon-secondary"><light-icon icon="download" /></div>
  <div class="icon-tertiary"><light-icon icon="brand-npm" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

## VS Code 操作

- 在 Solution Explorer 右鍵專案
- 選 Add NuGet Package
- 搜尋套件名稱
- 選版本並安裝

## 對應 CLI

```bash
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
dotnet list package
```

<div class="mt-6 text-sm opacity-75">
NuGet 是 .NET 的套件生態系，類似 JavaScript 的 npm。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/testing-publish.svg
---

# 第一個測試

<div class="slide-illo small">
  <div class="icon-primary"><light-icon icon="test-pipe" /></div>
  <div class="icon-secondary"><light-icon icon="checkbox" /></div>
  <div class="icon-tertiary"><light-icon icon="flask" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```bash
dotnet new xunit -n TodoApi.Tests
dotnet add TodoApi.Tests reference TodoApi
dotnet test
```

```csharp [TodoTests.cs]
public class TodoTests
{
    [Fact]
    public void NewTodo_IsNotDone_ByDefault()
    {
        var todo = new TodoItem(1, "Learn .NET", false);

        Assert.False(todo.IsDone);
    }
}
```

<div class="mt-6 text-sm opacity-75">
C# Dev Kit 會在 Testing 面板顯示測試，能單獨執行或 Debug。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/learning-map.svg
---

# Solution 管理多專案

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="folders" /></div>
  <div class="icon-secondary"><light-icon icon="git-merge" /></div>
  <div class="icon-tertiary"><light-icon icon="sitemap" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```bash
dotnet new sln -n DotnetLearning
dotnet sln add TodoApi/TodoApi.csproj
dotnet sln add TodoApi.Tests/TodoApi.Tests.csproj
```

```mermaid
%%{init: {"theme": "base", "themeVariables": {"fontFamily": "Noto Sans TC, Inter, sans-serif", "primaryColor": "#e8fbf8", "primaryTextColor": "#123b4a", "primaryBorderColor": "#0e9f9a", "lineColor": "#80cbc4", "secondaryColor": "#fff8e1", "tertiaryColor": "#f6fffe"}}}%%
flowchart TB
  S["DotnetLearning.sln"]
  A["TodoApi"]
  T["TodoApi.Tests"]

  S --> A
  S --> T
  T -. reference .-> A

  classDef solution fill:#fff8e1,stroke:#f3b33d,color:#123b4a,stroke-width:2px;
  classDef project fill:#e8fbf8,stroke:#0e9f9a,color:#123b4a,stroke-width:2px;
  classDef test fill:#f6fffe,stroke:#135483,color:#123b4a,stroke-width:2px;
  class S solution;
  class A project;
  class T test;
  linkStyle 0,1 stroke:#0e9f9a,stroke-width:3px;
  linkStyle 2 stroke:#135483,stroke-width:3px,stroke-dasharray: 6 5;
```

<div class="mt-6 text-sm opacity-75">
Solution 是工作區清單；大型專案通常會拆成 API、Domain、Infrastructure、Tests。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/testing-publish.svg
---

# 發佈 Publish

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="rocket" /></div>
  <div class="icon-secondary"><light-icon icon="cloud-upload" /></div>
  <div class="icon-tertiary"><light-icon icon="package" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```bash
dotnet publish -c Release -o ./publish
```

產出會包含：

<v-clicks>

- 編譯後的 DLL / executable
- 設定檔
- 相依套件
- 可部署到 VM、Container、PaaS 的檔案

</v-clicks>

<div class="mt-8 text-sm opacity-75">
學會本機 publish 後，再進一步學 Docker、CI/CD、雲端部署。
</div>

---
layout: dynamic-image
left: false
image: /illustrations/tools-setup.svg
---

# 常見錯誤排查

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="alert-triangle" /></div>
  <div class="icon-secondary"><light-icon icon="tool" /></div>
  <div class="icon-tertiary"><light-icon icon="shield-check" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

| 狀況 | 檢查 |
| --- | --- |
| VS Code 沒有提示 | C# Dev Kit 是否啟用、SDK 是否安裝 |
| `dotnet` 找不到 | PATH 是否包含 .NET SDK |
| `net9.0` 不支援 | `dotnet --list-sdks` 是否有 9.x |
| HTTPS 失敗 | 開發憑證是否信任 |
| Port 被占用 | 換 port 或關掉舊 process |

---
layout: dynamic-image
left: false
image: /illustrations/learning-map.svg
---

# 練習路線

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="map" /></div>
  <div class="icon-secondary"><light-icon icon="target" /></div>
  <div class="icon-tertiary"><light-icon icon="award" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

<v-clicks>

1. 建立 Console App，印出自己的名字
2. 建立 `Product` record 與計算稅金的方法
3. 建立 Todo Minimal API
4. 加入 GET / POST / DELETE
5. 用 VS Code Debug POST endpoint
6. 建立 xUnit 測試
7. `dotnet publish` 並檢查輸出

</v-clicks>

---
layout: dynamic-image
left: false
image: /illustrations/learning-map.svg
---

# 推薦學習順序

<div class="slide-illo top small">
  <div class="icon-primary"><light-icon icon="calendar-event" /></div>
  <div class="icon-secondary"><light-icon icon="route" /></div>
  <div class="icon-tertiary"><light-icon icon="book" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

```mermaid
%%{init: {"theme": "base", "themeVariables": {"fontFamily": "Noto Sans TC, Inter, sans-serif", "primaryColor": "#e8fbf8", "primaryTextColor": "#123b4a", "primaryBorderColor": "#0e9f9a", "lineColor": "#80cbc4", "secondaryColor": "#fff8e1", "tertiaryColor": "#f6fffe"}}}%%
flowchart LR
  A["C# 基礎"] --> B[".NET CLI"]
  B --> C["ASP.NET Core"]
  C --> D["EF Core"]
  C --> E["測試"]
  D --> F["部署"]
  E --> F

  classDef foundation fill:#fff8e1,stroke:#f3b33d,color:#123b4a,stroke-width:2px;
  classDef core fill:#e8fbf8,stroke:#0e9f9a,color:#123b4a,stroke-width:2px;
  classDef branch fill:#f6fffe,stroke:#8bd8d1,color:#123b4a,stroke-width:2px;
  classDef finish fill:#eaf2ff,stroke:#135483,color:#123b4a,stroke-width:2px;
  class A foundation;
  class B,C core;
  class D,E branch;
  class F finish;
  linkStyle 0,1,2,3,4,5 stroke:#0e9f9a,stroke-width:3px;
```

<div class="mt-8 text-left">

- 第 1 週：C#、Console、CLI、Debug
- 第 2 週：Minimal API、HTTP、OpenAPI
- 第 3 週：資料庫、EF Core、設定檔
- 第 4 週：測試、發佈、部署

</div>

---
layout: dynamic-image
left: false
image: /illustrations/learning-map.svg
---

# 參考資料

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="book" /></div>
  <div class="icon-secondary"><light-icon icon="external-link" /></div>
  <div class="icon-tertiary"><light-icon icon="bookmark" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

- Microsoft Learn: .NET 9 新功能
- Microsoft Learn: ASP.NET Core 9 新功能
- Microsoft Learn: C# Dev Kit for Visual Studio Code
- VS Code Marketplace: C# Dev Kit
- NuGet.org

<div class="mt-10 text-sm opacity-70">
真正的學習節奏：先讓專案跑起來，再逐步理解每一層。
</div>

---
layout: center-image
image: /illustrations/dotnet-hero.svg
---

# 下一步

<div class="slide-illo">
  <div class="icon-primary"><light-icon icon="rocket" /></div>
  <div class="icon-secondary"><light-icon icon="device-laptop" /></div>
  <div class="icon-tertiary"><light-icon icon="circle-check" /></div>
  <div class="slide-illo-line one"></div>
  <div class="slide-illo-line two"></div>
</div>

打開 VS Code，建立你的第一個 `TodoApi`

<div class="mt-8 text-lg opacity-75">
從能跑開始，讓理解慢慢長出來。
</div>
