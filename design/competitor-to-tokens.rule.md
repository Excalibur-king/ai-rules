# 规则：竞品 UI → Design Tokens 自动抽取

## 输入
- 产品名称 / 官网 URL / 截图
- 使用平台（Web / Mobile）

## 输出
必须生成一个 JSON，包含：
- semanticTokens
- componentTokens
- notes.assumptions（推断前提）
- notes.uncertain（不确定项）

## 抽取规则

### 颜色
- 使用语义分组：背景 / 文本 / 品牌 / 边框 / 状态
- 背景必须体现层级（page / container / elevated）
- 状态色需从品牌色推导

### 间距
- 使用尺度体系（scale）
- 禁止零散、不规则数值
- 优先 4 或 8 的倍数

### 排版
- 字体族如可识别需明确
- 字号需形成层级系统
- 行高必须语义化（紧凑 / 标准 / 宽松）

### 组件 Token
- 只抽取稳定、重复出现的组件
- 组件 Token 不允许直接引用颜色值
- 优先描述尺寸、内边距、圆角等结构属性

## 说明
- 所有推断内容必须写入 assumptions
- 所有模糊点必须写入 uncertain

## 严格禁止
- 使用竞品品牌命名 Token
- 在 Token 外部使用十六进制颜色
