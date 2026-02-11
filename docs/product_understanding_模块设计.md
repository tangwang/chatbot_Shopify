# product_understanding 模块设计

## 1. 目标

基于 `products_analyzed.csv` 的既有标注结果，生成在线导购可直接消费的结构化知识：

1. 各维度分布统计
2. 维度归一化与映射
3. 店铺分布简介
4. 店铺欢迎语候选
5. 在线分布查询能力

## 2. 输入

- `product_understanding/output_logs/products_analyzed.csv`
- 核心字段：`category_path/tags/target_audience/usage_scene/season/...`

## 3. 输出

- `dimension_topk.json`
- `normalization_mapping.json`
- `distribution_digest.md`
- `welcome_messages.json`

## 4. 在线技能接口

## 4.1 product_distribution
- 输入：`dimension_type`, `dimension_value`
- 输出：该维度分布摘要 + 示例商品 markdown

## 4.2 product_search_fuzzy
- 输入：宽泛意图槽位
- 输出：临时推荐方向 + 候选商品集合

## 4.3 product_search_exact
- 输入：明确 query
- 输出：搜索结果满足度判断、改写 query、精选商品ID、摘要

## 5. 日志

- `Logs/product_understanding_*.log`
- 记录：统计口径、归一化映射版本、查询命中率
