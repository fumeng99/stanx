 📢 **关注 Twitter: [@Nadiinn5](https://twitter.com/Nadiinn5)** 获取更多机器人和工具！

**版本**: v6.1.0

StandX Perps 做市机器人，支持单账户和多账户运行，内置多种策略模式。

## 📁 项目文件

- `standx-bot.js`: 机器人核心程序
- `run-multi.js`: 多账户启动器 (同一窗口)
- `start-accounts.bat`: 多账户启动器 (独立窗口) [推荐]
- `accounts.txt`: 多账户配置
- `.env`: 基础配置

## 🚀 快速开始

### 1. 安装依赖

```bash
npm install
```

### 2. 配置环境

复制 `.env.example` 到 `.env` 并填入私钥（单账户模式需要）：

```ini
PRIVATE_KEY=0x你的私钥
# 可选代理
# PROXY_URL=http://user:pass@host:port
```

### 3. 运行

**单账户模式**:
```bash
npm start
```

**多账户模式**:
1.  复制 `accounts.example.txt` 到 `accounts.txt`。
2.  填入账户信息，格式: `私钥----代理URL`。
3.  运行:
    -   **Windows (推荐)**: 双击 `start-accounts.bat` (每个账户独立窗口)
    -   **命令行**: `npm run multi` (所有账户在同一窗口)

## 📊 策略模式

启动时可选择以下模式：

1.  **网格模式 + 激进 (推荐)**
    -   积分效率: 100% + Maker Uptime 奖励
    -   挂单距离: 5-10 bps
    -   适合: 追求最大收益

2.  **网格模式 + 保守**
    -   积分效率: 50%
    -   挂单距离: 10-30 bps
    -   适合: 剧烈波动市场

3.  **单档模式**: 传统的单笔挂单模式

## 📈 网格策略说明

程序会根据余额自动调整网格档数：
-   < $50: 1 档
-   $50-150: 3 档
-   $150-300: 4 档
-   $300-500: 5 档
-   \> $500: 6-10 档

**功能特点**:
-   自动损耗保护
-   自动重连和错误恢复
-   防止重复交易
-   Maker Uptime 统计
