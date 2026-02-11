# evaluation 评测规范

## 1. 目的

针对 LLM 不确定性，建立可重复的评测闭环，用于评估：

- 编排器计划质量
- 导购回复质量
- 搜索结果适配度

## 2. 评测维度

1. 槽位抽取完整度
2. 问题质量（是否用户立场）
3. 推荐相关性
4. 推荐理由质量
5. 工具调用合理性（尤其 web_search）
6. 对话推进与转化潜力

## 3. 评测方法

- Rule-based 指标：字段完整率、JSON 解析率、工具调用约束命中率
- LLM-as-judge：按 rubric 评分（1-5）
- 人工抽检：高风险样本复核

## 4. 数据集建议

- 早期意图模糊：40条
- 需求逐步收敛：40条
- 明确检索意图：30条
- 多商品对比决策：20条
- 趋势/新概念触发：20条

## 5. 输出

- `evaluation/reports/orchestrator_eval.json`
- `evaluation/reports/assistant_eval.json`
- `evaluation/reports/search_eval.json`
- 每日回归趋势（可选）
