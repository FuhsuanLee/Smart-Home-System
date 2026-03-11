# 🎄 智慧家居系統（Smart Home System）

本專案為一個基於 **Embedded Linux** 的智慧家居系統，整合 **GPIO 控制、環境感測、影像驗證、Kernel Driver 紀錄以及遠端授權機制**，模擬實際智慧家居應用情境。

系統透過多模組整合，使家居設備不只是被動控制，而能依據環境條件與安全機制進行智慧化操作。

## 📖 專案簡介

本專案以 **聖誕節智慧家居情境** 為設計背景，模擬一個能夠控制裝飾燈、感知環境、並確保門控安全的智慧系統。

系統具備以下功能：

- 控制 LED 燈光（恆亮 / 閃爍）
- 透過光敏電阻感測環境亮度
- 使用 Camera 進行影像驗證
- 透過 Kernel Driver 記錄系統操作
- 結合手機端遠端授權機制

本專案重點在於展示 **嵌入式系統整合能力與系統層設計概念**

## 🏗 系統架構

系統主要由以下模組組成：

<img width="1506" height="700" alt="image" src="https://github.com/user-attachments/assets/5be97dc0-22b6-439f-96e9-e0f7e13bccfe" />

## ⚙️ 系統功能

**1️⃣ GUI 操作介面**

- 提供智慧家居主要操作中心
- 提供多組功能快捷鍵
- 顯示 LED 與門控狀態
- 提供資料輸入與系統控制

**2️⃣ GPIO LED 控制**

- 使用 GPIO 控制多顆 LED
- 支援恆亮與閃爍模式
- 透過燈光顯示系統狀態，例如：
  - 歡迎
  - 離開
  - 系統回饋

**3️⃣ 光敏電阻環境感測**

- 使用 **光敏電阻 + MCP3008 ADC**
- 即時讀取環境亮度
- 作為系統啟動與門控驗證的判斷條件

**4️⃣ Camera 視覺驗證（進階功能）**

- 在特定條件成立時啟動 Camera
- 偵測指定顏色或動態
- 作為門控安全的進階驗證機制

**5️⃣ Kernel Driver 黑盒子紀錄**

- 透過 Linux Kernel Driver 記錄系統操作
- 使用 ioctl 傳遞控制指令
- 記錄內容包含：
  - 操作時間
  - 指令內容
  - 執行結果
- 可透過使用者端讀取系統紀錄

**6️⃣ 遠端協同授權**

- 提供手機端 Web Authorize 按鈕
- 系統需同時通過：
  - 本地 GUI 操作
  - 遠端授權確認
- 提升門控安全性

## 🛠 使用技術

| **類別** | **技術** |
| --- | --- |
| 作業系統 | Embedded Linux |
| 程式語言 | C / C++ / Python / JavaScript |
| 硬體控制 | GPIO |
| 感測器 | 光敏電阻 + MCP3008 |
| 影像模組 | USB / CSI Camera |
| Web 技術 | Node.js / HTML |
| Driver | Linux Kernel Driver |
| 系統通訊 | ioctl |

## 📂 專案結構

```bash
smart-home-system
│
├── gui/              # GUI 操作介面
├── gpio_control/     # GPIO 控制程式
├── sensor/           # 光敏電阻與 ADC 讀取
├── camera/           # Camera 驗證模組
├── driver/           # Kernel Driver
├── web_auth/         # 遠端授權伺服器
├── scripts/          # 輔助腳本
│
└── README.md
```

## 🚀 執行方式

**1️⃣ 讀取感測器資料**

```bash
  python get_adc.py
```

**2️⃣ 啟動主程式**

```bash
  ./main
```

**3️⃣ 載入 Kernel Driver**

```bash
  sudo insmod driver.ko
```

**4️⃣ 啟動遠端授權伺服器**

```bash
  node server.js
```
