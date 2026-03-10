# 夜间 WhatsApp 复活

**仓库:** awesome-openclaw-usecases-moltbook  
**分类:** 夜间自动化  
**编号:** #14

---

## 🎯 痛点

关系需要维护。自动回复防止消息被遗忘，保持联系温热。

- 工作消息没有及时回复
- 冷友谊逐渐变淡
- 想不起上次联系是什么时候

---

## ⚡ 核心功能

1. **自动扫描** - 每5分钟扫描未读消息
2. **消息分类** - 按发送者和紧急程度分类
3. **自动回复** - 工作消息确认、冷友谊复活消息
4. **关系追踪** - 记录对话历史

---

## 🛠️ 所需技能

| 技能 | 用途 |
|------|------|
| `whatsapp` | 读取/回复消息 |
| `memory` | 追踪对话历史 |

---

## ⚙️ 消息分类配置

```javascript
const categories = {
  urgent: { response: "I'll have my human reply ASAP", maxAge: 0 },
  work: { response: "Acknowledged, will follow up", maxAge: 2 },
  friend: { response: "Hey! How have you been?", maxAge: 7 }
};
```

---

## 📝 Prompt 模板

```
## Night WhatsApp Revival

Every 5 minutes:
1. Scan WhatsApp Web for unreads
2. Categorize by sender and urgency
3. Reply to work: acknowledge with timeline
4. Reply to friends after 7 days: casual check-in
5. Log all sent messages to memory/whatsapp/

Safety:
- No financial transactions
- No personal/confidential info
- Flag sensitive topics for human review
```

---

## ⏰ Cron 配置

```json
{
  "schedule": "*/5 * * * *",
  "task": "whatsapp_revival"
}
```

---

## 🎯 成功指标

- 工作消息响应时间 <1 小时
- 没有友谊超过 14 天变冷
- 零不当自动回复

---

## ⚠️ 安全规则

1. **不处理财务** - 绝不自动处理金钱相关话题
2. **不透露隐私** - 不在自动回复中透露个人信息
3. **标记敏感** - 将敏感话题标记给人工审核
4. **学习关系** - 记录每个人的偏好和历史

---

*用例来源: awesome-openclaw-usecases-moltbook | 整理时间: 2026-03-09*
