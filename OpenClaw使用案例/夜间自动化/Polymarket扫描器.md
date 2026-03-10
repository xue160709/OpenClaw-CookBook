# Polymarket 扫描器

**分类:** 夜间自动化  
**编号:** #16

## 🎯 痛点
- 预测市场信息变化快，人工监控耗时
- 错过高置信度交易机会
- 需要同时关注多个市场/事件

## ⚡ 核心功能
1. 扫描Polymarket上指定主题的预测市场
2. 监控市场赔率变化，发现套利机会
3. 检测高置信度预测（赔率>80%或<20%）
4. 设置价格异动告警
5. 生成每日市场摘要报告

## 🛠️ 所需技能
| 技能 | 用途 |
|------|------|
| web爬虫 | 抓取Polymarket市场数据 |
| 监控 | 跟踪赔率变化 |

## 📝 Prompt 模板
```
你是预测市场扫描助手。请监控Polymarket上的指定预测市场。

任务：
1. 抓取 Polymarket API 获取市场数据：
   ```bash
   curl "https://clob.polymarket.com/markets?active=true&closed=false"
   ```
2. 筛选用户关注的主题（如：Crypto、Politics、Sports等）
3. 分析各市场的：
   - 当前赔率（Probabilities）
   - 交易量（Volume）
   - 流动性（Liquidity）
   - 到期时间
4. 标记高置信度机会：
   - 赔率 > 80% 或 < 20%
   - 交易量 > $10,000
5. 检测赔率突变（较昨日变化 > 10%）

生成报告：
```json
{
  "scan_time": "...",
  "high_confidence": [...],
  "price_changes": [...],
  "recommendations": [...]
}
```
```
