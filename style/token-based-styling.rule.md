# 规则：基于 Token 的样式生成

## 原则
- 所有间距来自 spacing Tokens
- 所有颜色来自 antd 主题 Token
- 所有排版来自 typography Tokens

## 允许
- 使用 antd token 消费
- 使用 CSS-in-JS 访问 Token

## 严格禁止
- 行内样式
- 写死数值
- 覆盖 antd 内部类名

## 校验标准
任何样式若无法追溯到 Token，
即视为不合规。
