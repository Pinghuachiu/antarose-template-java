# Antarose Template - Backend (Spring Boot 3)

## 技術棧

- **Java**: 21
- **Framework**: Spring Boot 3.3.5
- **Build Tool**: Gradle 8.10.2
- **Database**: H2 (In-Memory)
- **ORM**: Spring Data JPA

## 快速開始

### 前置需求

- Java 21 或更高版本
- Gradle 8.x（已包含 Gradle Wrapper）

### 安裝與執行

```bash
# 進入後端目錄
cd backend

# 使用 Gradle Wrapper 執行（首次會自動下載 Gradle）
./gradlew bootRun

# Windows 使用
gradlew.bat bootRun
```

### 編譯專案

```bash
# 編譯
./gradlew build

# 執行測試
./gradlew test

# 清理編譯產物
./gradlew clean
```

## API 端點

- **Health Check**: `GET http://localhost:5060/api/health`
- **Hello**: `GET http://localhost:5060/api/hello?name=YourName`
- **H2 Console**: `http://localhost:5060/h2-console`

## 專案結構

```
backend/
├── src/
│   ├── main/
│   │   ├── java/com/antarose/template/
│   │   │   ├── TemplateApplication.java      # 主程式
│   │   │   ├── controller/                    # REST 控制器
│   │   │   │   ├── HealthController.java
│   │   │   │   └── HelloController.java
│   │   │   └── model/                         # 資料模型
│   │   │       └── User.java
│   │   └── resources/
│   │       └── application.yml                # 配置檔
│   └── test/                                  # 測試檔案
├── build.gradle                               # Gradle 配置
├── settings.gradle                            # Gradle 設定
└── gradlew                                    # Gradle Wrapper
```

## 開發

### 新增依賴

編輯 `build.gradle`：

```gradle
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-xxx'
}
```

### 環境變數

複製 `.env.example` 為 `.env.local` 並修改配置。

## 資料庫

預設使用 H2 In-Memory Database，可透過以下連線資訊存取：

- **JDBC URL**: `jdbc:h2:mem:testdb`
- **Username**: `sa`
- **Password**: （空白）
- **Console**: `http://localhost:5060/h2-console`
