# Scoop 安装教程（Windows 包管理器）

> 简洁、强大、适合开发者使用的命令行软件安装工具

[![Tests](https://github.com/chuan0712/Scoop-apps/actions/workflows/ci.yml/badge.svg)](https://github.com/chuan0712/Scoop-apps/actions/workflows/ci.yml)
[![Excavator](https://github.com/chuan0712/Scoop-apps/actions/workflows/excavator.yml/badge.svg)](https://github.com/chuan0712/Scoop-apps/actions/workflows/excavator.yml)


这是我维护的 Scoop bucket，包含若干工具的 manifests 文件……

---

## 🟢 一、安装前准备

### ✅ 系统要求：
- Windows 7 及以上（推荐 Windows 10/11）
- PowerShell 5 或更高版本
- [.NET Framework 4.5+](https://dotnet.microsoft.com/)（大部分系统已自带）

---

## 🚀 二、快速安装 Scoop（默认路径）

1. 打开 **PowerShell**（推荐以管理员身份运行）
2. 执行以下命令：

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
irm get.scoop.sh | iex
```

如果 `irm` 被屏蔽，也可以使用：

```powershell
Invoke-RestMethod get.scoop.sh | Invoke-Expression
```

---

## ⚙️ 三、自定义安装路径（可选）

若你想将 Scoop 安装到自定义路径，例如 `D:\Scoop`：

```powershell
irm get.scoop.sh -outfile 'install.ps1'
.\install.ps1 -ScoopDir 'C:\Scoop' -ScoopGlobalDir 'C:\Scoop\Global' -NoProxy
```

- `-ScoopDir`：用户级应用目录
- `-ScoopGlobalDir`：系统级应用目录（需管理员权限）

---

## 📦 四、安装软件示例

安装 Git：

```powershell
scoop install git
```

安装常用工具：

```powershell
scoop install 7zip git aria2 sudo
```

---

## 🪣 五、添加额外应用源（Buckets）

Scoop 默认只包含 `main` 源，如需更多软件：

```powershell
scoop bucket add extras
scoop bucket add versions
scoop bucket add java
```

例如安装 Typora（extras 源中）：

```powershell
scoop install typora
```

---

## 🔄 六、更新与维护

更新 Scoop 本体：

```powershell
scoop update
```

更新所有已安装软件：

```powershell
scoop update *
```

清理旧版本缓存：

```powershell
scoop cleanup *
```

---

## ❗ 七、常见问题排查

### 问题 1：无法下载软件？

配置一下 Aria2 的参数:

```powershell
scoop config aria2-args @(
  '--split=16',
  '--max-connection-per-server=16',
  '--min-split-size=1M',
  '--timeout=30',
  '--retry-wait=5',
  '--max-tries=5',
  '--console-log-level=warn'
)
```

### 问题 2：权限不足？

设置执行策略：

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

或者以管理员身份运行 PowerShell。

---

## ✅ 检查是否安装成功

```powershell
scoop --version
```

如果返回如 `Scoop v0.x.x`，表示 Scoop 安装成功！

---

**祝你安装顺利，玩转 Scoop！如需自动安装脚本或定制配置，请随时留言 🙌**
