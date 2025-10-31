# Antarose Template - Java Full Stack

A production-ready full-stack template featuring Spring Boot 3 + Java backend and Next.js 15 frontend.

[![Java](https://img.shields.io/badge/Java-21-orange)](https://adoptium.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.3.5-green)](https://spring.io/projects/spring-boot)
[![Next.js](https://img.shields.io/badge/Next.js-15.5-black)](https://nextjs.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📋 目錄

- [概述](#概述)
- [快速開始](#快速開始)
- [專案結構](#專案結構)
- [後端 (Spring Boot)](#後端-spring-boot)
- [前端 (Next.js)](#前端-nextjs)
- [開發工作流程](#開發工作流程)
- [生產環境部署](#生產環境部署)
- [疑難排解](#疑難排解)

---

## 概述

此模板提供建構現代化 Web 應用程式的堅實基礎：

### ✨ 核心技術

**後端 (Backend)**
- **Spring Boot 3** - 企業級 Java 應用框架
- **Java 21** - 最新 LTS 版本
- **Spring Data JPA** - 資料持久化
- **Gradle 8** - 建置工具
- **H2 Database** - 內嵌式資料庫 (可替換為 PostgreSQL/MySQL)

**前端 (Frontend)**
- **Next.js 15** - React 框架 (App Router)
- **React 19** - 使用者介面函式庫
- **Tailwind CSS** - Utility-first CSS 框架
- **shadcn/ui** - 高品質元件庫
- **TypeScript** - 型別安全

### 🎯 功能特色

- ✅ **前後端分離架構** - 獨立開發與部署
- ✅ **Spring Data JPA** - ORM 資料庫抽象層
- ✅ **RESTful API** - 標準化 API 設計
- ✅ **型別安全** - Java Strong Typing + TypeScript
- ✅ **熱重載開發** - Spring DevTools + Next.js Fast Refresh
- ✅ **測試框架** - JUnit 5 (後端) + Jest (前端)
- ✅ **一鍵專案初始化** - 自動化腳本

---

## 快速開始

### 方式一：使用初始化腳本 (推薦) 🚀

**下載並執行腳本：**

```bash
# 方法 1: 下載後執行
curl -O https://raw.githubusercontent.com/Pinghuachiu/antarose-template-java/main/anta-java.sh
chmod +x anta-java.sh
./anta-java.sh my-awesome-project

# 方法 2: 直接執行 (一行命令)
curl -fsSL https://raw.githubusercontent.com/Pinghuachiu/antarose-template-java/main/anta-java.sh | bash -s my-awesome-project
```

**腳本會自動執行以下操作：**

| 步驟 | 說明 |
|------|------|
| ✅ 環境檢查 | 驗證 Git, Java 21+, Node.js, npm 是否安裝 |
| ✅ Clone 模板 | 從 GitHub 複製最新版本 |
| ✅ 清理檔案 | 移除 .git 歷史記錄和模板專用檔案 |
| ✅ 更新配置 | 修改專案名稱、描述、作者資訊 |
| ✅ 建置專案 | 使用 Gradle 建置 Spring Boot 專案 |
| ✅ 安裝依賴 | 安裝前後端所需套件 (可選) |
| ✅ 初始化 Git | 建立新的 Git repository |

**互動式設定：**

```
? Project description: (預設: A Java Spring Boot project built with Antarose Template)
? Author: (預設: jackalchiu@antarose.com)
? GitHub repository URL: (可選，直接按 Enter 跳過)
? Install dependencies now?: (Y/n)
```

### 方式二：手動安裝

#### 1. Clone Repository

```bash
git clone https://github.com/Pinghuachiu/antarose-template-java.git my-project
cd my-project
rm -rf .git
git init
```

#### 2. 安裝依賴

**後端：**
```bash
cd backend
./gradlew build
```

**前端：**
```bash
cd frontend
npm install
```

#### 3. 啟動開發伺服器

**Terminal 1 - 後端 (Port 5060):**
```bash
cd backend
./gradlew bootRun
```

**Terminal 2 - 前端 (Port 5050):**
```bash
cd frontend
npm run dev
```

#### 4. 訪問應用

- 🌐 **前端**: http://localhost:5050
- 🔌 **後端 API**: http://localhost:5060
- ❤️ **健康檢查**: http://localhost:5060/api/health
- 👋 **Hello API**: http://localhost:5060/api/hello
- 💾 **H2 Console**: http://localhost:5060/h2-console

---

## 專案結構

```
antarose-template-java/
├── backend/                     # Spring Boot 後端
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/antarose/template/
│   │   │   │   ├── TemplateApplication.java    # 主程式
│   │   │   │   ├── controller/                 # REST 控制器
│   │   │   │   │   ├── HealthController.java
│   │   │   │   │   └── HelloController.java
│   │   │   │   └── model/                      # JPA 實體
│   │   │   │       └── User.java
│   │   │   └── resources/
│   │   │       └── application.yml             # 配置檔
│   │   └── test/                               # 測試檔案
│   ├── build.gradle                            # Gradle 配置
│   ├── settings.gradle
│   ├── gradlew                                 # Gradle Wrapper
│   ├── .env.example                            # 環境變數範本
│   └── README.md
│
├── frontend/                    # Next.js 前端
│   ├── app/                     # App Router
│   │   ├── layout.tsx           # 根佈局
│   │   ├── page.tsx             # 首頁
│   │   ├── about/               # About 頁面
│   │   ├── error.tsx            # 錯誤邊界
│   │   └── not-found.tsx        # 404 頁面
│   ├── components/              # React 元件
│   │   ├── ui/                  # shadcn/ui 元件
│   │   └── layout/              # 佈局元件
│   ├── lib/
│   │   ├── utils.ts             # 工具函數
│   │   └── api-client.ts        # API 客戶端
│   ├── package.json
│   ├── .env.example             # 前端環境變數
│   └── README.md
│
├── docs/                        # 文檔
│   └── architecture/            # 架構文件
├── anta-java.sh                 # 專案初始化腳本
├── README.md                    # 此檔案
└── .gitignore
```

---

## 後端 (Spring Boot)

### 技術棧

| 技術 | 版本 | 用途 |
|------|------|------|
| Spring Boot | 3.3.5 | 應用框架 |
| Java | 21 | 程式語言 |
| Spring Data JPA | 3.3.x | ORM |
| H2 Database | 2.x | 內嵌資料庫 |
| Gradle | 8.10.2 | 建置工具 |
| Lombok | Latest | 減少樣板代碼 |

### API 端點

| 方法 | 路徑 | 說明 |
|------|------|------|
| GET | `/api/health` | 健康檢查 |
| GET | `/api/hello` | Hello World (預設) |
| GET | `/api/hello?name=John` | 個人化問候 |
| GET | `/h2-console` | H2 資料庫控制台 |

### 環境變數設定

建立 `backend/.env.local` 檔案：

```env
# Server Configuration
SERVER_PORT=5060

# Database Configuration
DB_URL=jdbc:h2:mem:testdb
DB_USERNAME=sa
DB_PASSWORD=

# Application Configuration
SPRING_PROFILES_ACTIVE=dev
```

### 新增 API 端點

1. **建立控制器** `backend/src/main/java/com/antarose/template/controller/UserController.java`:

```java
package com.antarose.template.controller;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.HashMap;
import java.util.Map;

@RestController
@RequestMapping("/api/users")
public class UserController {

    @GetMapping
    public ResponseEntity<Map<String, Object>> getUsers() {
        Map<String, Object> response = new HashMap<>();
        response.put("users", new ArrayList<>());
        return ResponseEntity.ok(response);
    }
}
```

### 資料庫操作

**建立實體** `backend/src/main/java/com/antarose/template/model/Post.java`:

```java
package com.antarose.template.model;

import jakarta.persistence.*;
import lombok.Data;

import java.time.LocalDateTime;

@Entity
@Table(name = "posts")
@Data
public class Post {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false, length = 200)
    private String title;

    @Column(columnDefinition = "TEXT")
    private String content;

    @Column(name = "created_at")
    private LocalDateTime createdAt;
}
```

### 執行測試

```bash
cd backend
./gradlew test
```

### 建置專案

```bash
cd backend
./gradlew build
```

---

## 前端 (Next.js)

### 技術棧

| 技術 | 版本 | 用途 |
|------|------|------|
| Next.js | 15.5.6 | React 框架 |
| React | 19 | UI 函式庫 |
| TypeScript | 5.x | 型別系統 |
| Tailwind CSS | 3.x | CSS 框架 |
| shadcn/ui | Latest | 元件庫 |

### 環境變數設定

建立 `frontend/.env.local` 檔案：

```env
NEXT_PUBLIC_API_URL=http://localhost:5060
```

### API 整合範例

```typescript
// frontend/app/example/page.tsx
'use client'

import { useEffect, useState } from 'react'

export default function ExamplePage() {
  const [data, setData] = useState(null)

  useEffect(() => {
    fetch(`${process.env.NEXT_PUBLIC_API_URL}/api/hello`)
      .then(res => res.json())
      .then(setData)
  }, [])

  return <div>{JSON.stringify(data)}</div>
}
```

---

## 開發工作流程

### Git Flow 分支策略

```
main          (生產環境)
  └── develop (開發環境)
        └── feature/feature-name (功能開發)
        └── bugfix/bug-name (錯誤修復)
```

### 開發流程

1. **建立功能分支**
```bash
git checkout develop
git checkout -b feature/new-feature
```

2. **開發與測試**
```bash
# 後端測試
cd backend && ./gradlew test

# 前端測試
cd frontend && npm run lint
```

3. **提交變更**
```bash
git add .
git commit -m "feat: add new feature"
```

4. **合併回 develop**
```bash
git checkout develop
git merge --no-ff feature/new-feature
git push origin develop
```

---

## 生產環境部署

### 後端部署

**建立 JAR 檔案:**

```bash
cd backend
./gradlew bootJar
java -jar build/libs/antarose-template-backend-1.0.0.jar
```

**使用 Docker:**

```dockerfile
FROM eclipse-temurin:21-jdk-alpine

WORKDIR /app
COPY build/libs/*.jar app.jar

EXPOSE 5060
ENTRYPOINT ["java", "-jar", "app.jar"]
```

### 前端部署

```bash
cd frontend
npm run build
npm start
```

---

## 疑難排解

### Port 已被佔用

```bash
# 檢查 Port 5060 (後端)
lsof -ti:5060 | xargs kill -9

# 檢查 Port 5050 (前端)
lsof -ti:5050 | xargs kill -9
```

### CORS 錯誤

檢查 Spring Boot 的 CORS 配置，確認前端 URL 在允許列表中。

### Gradle 建置失敗

```bash
# 清理並重新建置
cd backend
./gradlew clean build
```

### 前端建置錯誤

```bash
cd frontend
rm -rf .next node_modules
npm install
npm run build
```

---

## 文檔資源

### 後端文檔
- [Spring Boot 官方文檔](https://spring.io/projects/spring-boot)
- [Spring Data JPA 文檔](https://spring.io/projects/spring-data-jpa)
- [Gradle 文檔](https://docs.gradle.org/)

### 前端文檔
- [Next.js 文檔](https://nextjs.org/docs)
- [React 文檔](https://react.dev/)
- [Tailwind CSS 文檔](https://tailwindcss.com/docs)
- [shadcn/ui 文檔](https://ui.shadcn.com)

### 專案文檔
- [後端詳細文檔](./backend/README.md)
- [前端詳細文檔](./frontend/README.md)
- [架構文件](./docs/architecture/)

---

## 授權條款

MIT License - 詳見 [LICENSE](LICENSE) 檔案

---

## 貢獻指南

歡迎提交 Issue 和 Pull Request！

1. Fork 此專案
2. 建立功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交變更 (`git commit -m 'feat: Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟 Pull Request

---

## 支援與反饋

- 📧 Email: jackalchiu@antarose.com
- 🐛 Issues: [GitHub Issues](https://github.com/Pinghuachiu/antarose-template-java/issues)
- 📚 Docs: [Documentation](./docs/)

---

**由 Antarose AI Tech Inc. 用心打造** ❤️
