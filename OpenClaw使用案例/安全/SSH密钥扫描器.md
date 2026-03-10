# SSH 密钥扫描器

**仓库:** awesome-openclaw-usecases-moltbook  
**分类:** 安全监控  
**编号:** #09

---

## 🎯 痛点

SSH 密钥经常被复制到错误的位置、提交到 git、或留下不安全的权限。自动化扫描在攻击者之前发现这些问题。

---

## ⚡ 核心功能

1. **文件系统扫描** - 扫描 ~/.ssh, ~/Downloads, 项目目录
2. **权限检查** - 检查密钥权限是否为 600
3. **Git 仓库检查** - 检查密钥是否被提交到 git
4. **位置检查** - 检查是否在标准 ~/.ssh 位置
5. **AWS 凭证扫描** - 检查明文 AWS 密钥

---

## 🛠️ 所需技能

| 技能 | 用途 |
|------|------|
| `filesystem` | 扫描目录 |
| `git` | 检查 git 仓库 |
| `telegram` | 安全告警 |

---

## ⚙️ 扫描配置

```json
{
  "scan_paths": [
    "~/.ssh",
    "~/Downloads",
    "~/projects",
    "~/workspace"
  ],
  "exclusions": [
    "node_modules",
    ".git/objects",
    "*.pub"
  ],
  "patterns": {
    "ssh_key": [
      "BEGIN OPENSSH PRIVATE KEY",
      "BEGIN RSA PRIVATE KEY",
      "BEGIN EC PRIVATE KEY"
    ],
    "aws_key": [
      "AKIA[0-9A-Z]{16}",
      "aws_access_key_id",
      "aws_secret_access_key"
    ]
  }
}
```

---

## 📝 Prompt 模板

```
## SSH Key Scanner

Weekly security scan (Sundays 02:00):
1. Scan all configured paths for SSH private keys
2. Check file permissions (must be 600)
3. Check if keys are in git repositories
4. Check for AWS credentials in plain text
5. Look for keys in non-standard locations
6. Generate security report
7. Send critical alerts immediately
8. Save report to memory/security-scans/YYYY-MM-DD.md

Critical alerts (immediate notification):
- SSH key found in git repo
- AWS credentials in plain text
- Private key with world-readable permissions

Remediation steps to include:
- chmod 600 for permission issues
- git rm --cached for committed keys
- mv to ~/.ssh/ for wrong locations
- AWS IAM key rotation for exposed keys
```

---

## ⏰ Cron 配置

```json
{
  "schedule": "0 2 * * 0",
  "task": "security_key_scan",
  "immediate_alert_threshold": "high"
}
```

---

## ⚠️ 风险等级定义

| 等级 | 场景 |
|------|------|
| 🚨 HIGH | 密钥在 git 仓库中、AWS 凭证明文 |
| ⚠️ MEDIUM | 权限不正确、非标准位置 |
| ✅ LOW | 标准位置、权限正确 |

---

*用例来源: awesome-openclaw-usecases-moltbook | 整理时间: 2026-03-09*
