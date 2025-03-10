### Cyd 天气时钟项目简介

这是一个基于 **ESP32-Cheap-Yellow-Display** 的 **天气时钟**，集成了 **室内外环境监测** 和 **天气提醒** 功能，适合放在家里或办公室，随时掌握天气状况。

---

### 🌟 **核心功能**

#### 📟 **1. 显示内容**

📌 **左侧屏幕**：

- 当前 **时间** 和 **日期**（同步NTP服务器，确保精准）
- **室内温湿度**（DHT22传感器实时检测）

📌 **右侧屏幕**：

- **城市位置**（通过IP大致定位）
- **室外天气**（晴天、多云、雨、雪等）
- **室外温度、湿度**（通过 **Open-Meteo API** 获取实时数据）

📌 **底部智能建议**：

- 结合天气和时间段，提供 **穿衣、出行提醒**
- 例如：「☔ 现在下雨，出门记得带伞！」

---

#### 📡 **2. 数据采集**

- **室内温湿度**：DHT22 传感器（连接在IO22）
- **室外天气**：Open-Meteo API，获取最近的天气状况
- **时间同步**：NTP 服务器，保证时钟精准

---

#### 🔔 **3. 智能提醒**

- 根据不同时间段（**早晨 / 中午 / 傍晚 / 夜间**），推送不同建议
- 结合天气状况（晴天、多云、雾、雨、雪、雷暴），提供合理出行提醒
- 遇到 **极端温度**（高于 **35°C** 或低于 **5°C**），给出特别警告

---

#### ⚙ **4. 自动化 & 智能刷新**

- **WiFi 自动重连**，防止断网影响功能
- **定期更新**：
  - **时间**：定期刷新
  - **天气**：间隔一段时间自动获取新数据
  - **传感器数据**：定期采集，变化时才刷新屏幕，节省资源

---

#### 🚨 **5. 可靠的错误处理**

- 监控 **WiFi 连接状态**，如果断网，屏幕会提示「网络连接异常」

---

### ⚙ **配置文件（PlatformIO）**

本项目使用 **PlatformIO** 进行构建，支持多种硬件配置，你可以根据自己的屏幕类型选择不同的 `env` 进行编译。例如：

- **cyd**：适用于 **ILI9341** 屏幕
- **cyd2usb**：适用于 **ST7789** 屏幕，带 **RGB 反转** 和 **BGR 颜色顺序** 调整

此外，`platformio.ini` 配置文件中包含了 **WiFi 信息、天气 API、时区、更新间隔、亮度** 等参数，你可以根据自己的需求进行调整。

