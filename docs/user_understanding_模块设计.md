# user_understanding 模块设计

## 1. 目标

基于前端 mock 行为数据，生成用户画像与个性化欢迎语，支持导购对话“懂人”。

## 2. 输入（mock）

- 点击/加购/购买记录（各最近20）
- 搜索记录（最近40）
- AI 对话压缩记录（最近40）
- 触发事件类型（进入/对话/站内事件）

## 3. 输出

1. markdown 用户画像
2. 个性化欢迎语
3. 可选：离线推荐列表

## 4. 画像结构

1. 慢变偏好：风格/尺码/人群/品牌态度
2. 半稳定场景：通勤/旅行/功能诉求
3. 硬约束：禁忌与雷区
4. 行为证据：每条结论需可追溯

## 5. 接口建议

- `POST /user-understanding/build-profile`
- `POST /user-understanding/gen-personal-welcome`
- `GET /user-understanding/profile/{user_id}`

## 6. 日志

- `Logs/user_understanding_*.log`
- 记录：输入规模、画像版本、更新时间、证据来源计数
