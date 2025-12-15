# 规则：多主题 Token 工厂结构

## 目标
支持多主题（深色 / 浅色 / 品牌变体），
且无需修改组件代码。

## Token 分层
- core：尺度、字体、基础规格（不可变）
- semantic：语义 Token（可变）
- component：组件结构 Token（引用 semantic）

## 主题规则
- 仅 semanticTokens 可随主题变化
- componentTokens 不得直接区分主题
- coreTokens 全主题共享

## 示例
- semantic.color.bg.page
- semantic.color.text.primary
- component.Button.radius.md

## 严格禁止
- 主题专属组件 Token
- 跨主题覆盖 Token
