# 钉钉 AI 助手

**分类:** 中国特色用例  
**难度:** ⭐⭐

---

## 🎯 痛点

- 企业内部协作需要多平台切换
- Stream 模式无需公网 IP 即可部署
- 审批流程自动化程度低
- 知识库查询不便

---

## ⚡ 核心功能

1. **钉钉机器人** - Stream 模式部署，无需公网域名
2. **消息自动回复** - 智能问答、业务查询
3. **审批流程** - 自动发起/处理审批
4. **群通知** - 定时推送消息到群
5. **知识库** - 连接钉钉知识库提供问答

---

## 🛠️ 所需技能

| 技能 | 用途 |
|------|------|
| `dingtalk` | 钉钉消息收发 |
| `dingtalk_stream` | Stream 模式接入 |
| `feishu_calendar` | 日程管理 (可复用) |
| `memory` | 知识库问答 |

---

## ⚙️ 部署配置 (Stream 模式)

```yaml
# openclaw.yaml
channels:
  - type: dingtalk
    mode: stream
    app_id: dingtalk_client_id
    app_secret: dingtalk_client_secret
    agent_id: agent_id
```

### 优势
- ✅ 无需公网域名
- ✅ 支持 Webhook 回调
- ✅ 自动维护 Token
- ✅ 支持加密消息

---

## 📝 Prompt 模板

```
你是一个钉钉 AI 助手，为企业提供智能服务。

功能范围：
1. 解答员工问题（政策、流程、技术）
2. 发起和跟进审批流程
3. 定时推送通知（日报、周报、提醒）
4. 集成企业知识库

请用中文回复，保持专业但友好的语气。
```

---

## ⏰ Cron 配置示例

```json
[
  { "schedule": "0 9 * * 1-5", "task": "work_reminder", "description": "工作日提醒" },
  { "schedule": "0 18 * * 5", "task": "week_summary", "description": "周五周报" }
]
```

---

## 💡 与飞书对比

| 特性 | 飞书 | 钉钉 |
|------|------|------|
| 部署难度 | ⭐⭐ | ⭐⭐ (Stream 模式简单) |
| 生态 | 文档/日历强 | 审批/企业管理强 |
| API 丰富度 | ⭐⭐⭐ | ⭐⭐⭐ |
| 国内企业适用 | ⭐⭐⭐ | ⭐⭐⭐ |

---

*用例来源: awesome-openclaw-usecases-zh | 整理时间: 2026-03-09*
