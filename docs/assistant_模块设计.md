# assistant 模块设计

## 1. 目标

assistant 模块负责“导购对话主流程”：

1. 首轮欢迎语选择
2. 每轮 Orchestrator 规划
3. 执行技能并聚合结果
4. 面向用户输出最终导购回复

## 2. 子模块

- `orchestrator.py`：产出结构化计划对象
- `responder.py`：消化工具结果并生成用户回复
- `prompts/`：编排器与导购提示词
- `schemas/`：计划对象 JSON schema

## 3. 输入输出

## 3.1 orchestrator 输入

- 用户输入文本
- 用户画像 markdown
- 最近 10 轮对话
- 商店分布摘要
- 场景上下文（地域/季节/天气）

## 3.2 orchestrator 输出

- `stage`
- `intent`（槽位）
- `tool_plan`（工具、优先级、参数、must）
- `questions_to_ask`
- `response_strategy`

## 3.3 responder 输入

- 原始用户输入
- orchestrator 计划对象
- 工具调用结果
- 会话历史

## 3.4 responder 输出

- 面向用户的自然语言回复
- 可选结构化商品结果（供前端渲染）

## 4. 关键流程

1. Planner 先行：生成 plan JSON
2. ToolExecutor 依 plan 执行技能
3. Responder 生成最终回复
4. 异步触发画像更新信号

## 5. 提示词要点

- Orchestrator：只输出 JSON，禁止解释文本
- Assistant：导购语气，补信息+推荐+轻引导
- 每轮最多 2 个问题，且必须用户立场

## 6. 日志

- `Logs/orchestrator_*.log`
- `Logs/assistant_*.log`
- 记录：输入摘要、计划 JSON、工具执行、最终回复
