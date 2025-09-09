# Claude Code 环境配置脚本

这是一个用于配置 Claude Code 开发环境的自动化脚本，**支持 macOS 和 Linux 系统**。

## 功能特性

- 🔧 自动检测 macOS/Linux 系统和 Shell 环境（zsh/bash/fish）
- 🔑 配置 Anthropic API 密钥和基础 URL
- 📝 自动更新 Shell 配置文件（~/.zshrc、~/.bashrc、~/.bash_profile 或 ~/.config/fish/config.fish）
- ⚙️ 自动更新 Claude 配置文件（~/.claude.json）
- 🔄 支持配置的清理和重新配置
- ✅ 配置验证和状态检查

## 系统要求

- **操作系统**: macOS 或 Linux（不支持 Windows）
- **Shell**: zsh、bash 或 fish
- **依赖工具**: jq（用于 JSON 处理）

## 安装依赖

如果系统中没有安装 `jq`，请先安装：

```bash
# macOS - 使用 Homebrew 安装
brew install jq

# Linux - 使用包管理器安装
# Ubuntu/Debian
sudo apt-get update && sudo apt-get install jq

# CentOS/RHEL/Fedora
sudo yum install jq
# 或者
sudo dnf install jq

# Arch Linux
sudo pacman -S jq
```

## 使用方法

### 基本语法

```bash
./claude-env-setup.sh <base-url> <api-key>
```

### 参数说明

- `base-url`: Anthropic API 的基础 URL（必需）
- `api-key`: Anthropic API 密钥（必需）

### 使用示例

#### 1. 使用默认 API 地址

```bash
./claude-env-setup.sh https://api.aicodemirror.com/api/claudecode your-api-key-here
```

#### 2. 使用自定义 API 地址

```bash
./claude-env-setup.sh https://your-custom-api.com/v1 your-api-key-here
```

#### 3. 使用官方 API 地址

```bash
./claude-env-setup.sh https://api.anthropic.com your-api-key-here
```

## 脚本功能

### 自动配置

脚本会自动执行以下操作：

1. **环境检测**: 检测操作系统和 Shell 类型
2. **配置备份**: 备份现有的 Shell 配置文件
3. **环境变量设置**: 在 Shell 配置文件中添加环境变量
4. **Claude 配置**: 更新 ~/.claude.json 配置文件
5. **配置验证**: 验证所有配置是否正确设置

### 环境变量

脚本会设置以下环境变量：

- `ANTHROPIC_BASE_URL`: API 基础 URL
- `ANTHROPIC_API_KEY`: API 密钥
- `ANTHROPIC_AUTH_TOKEN`: 认证令牌（空值）

### 配置文件

- **Shell 配置**: 
  - macOS: ~/.zshrc 或 ~/.bash_profile
  - Linux: ~/.zshrc、~/.bashrc 或 ~/.config/fish/config.fish
- **Claude 配置**: ~/.claude.json

## 使用后操作

配置完成后，需要重新加载 Shell 配置：

```bash
# 重新加载配置
# zsh
source ~/.zshrc

# bash
source ~/.bashrc
# 或
source ~/.bash_profile

# fish
source ~/.config/fish/config.fish

# 或者重新打开终端窗口
```

## 故障排除

### 1. 权限问题

如果遇到权限问题，请确保脚本有执行权限：

```bash
chmod +x claude-env-setup.sh
```

### 2. jq 未安装

如果提示 `jq` 命令未找到，请安装：

```bash
brew install jq
```

### 3. 配置验证失败

如果配置验证失败，请检查：

- API 密钥是否正确
- API 基础 URL 是否可访问
- 网络连接是否正常

### 4. 重新配置

如果需要重新配置，直接运行脚本即可，脚本会自动清理旧配置并写入新配置。

## 注意事项

- ⚠️ **支持 macOS 和 Linux 系统**（不支持 Windows）
- ⚠️ 脚本会修改 Shell 配置文件，建议先备份
- ⚠️ 请确保 API 密钥的安全性
- ⚠️ 配置完成后需要重新加载 Shell 配置或重启终端

## 支持

如果遇到问题，请检查：

1. 系统是否为 macOS 或 Linux
2. 是否安装了 jq
3. API 密钥和 URL 是否正确
4. 网络连接是否正常

---

**注意**: 此脚本支持 macOS 和 Linux 系统，不支持 Windows。
