# 规则：Design Tokens → antd Theme 适配

## 目标
输出 antd v5 ThemeConfig

## 映射规范

### 颜色
- semantic.color.text.primary → colorText
- semantic.color.text.secondary → colorTextSecondary
- semantic.color.bg.page → colorBgBase
- semantic.color.bg.container → colorBgContainer
- semantic.color.border.default → colorBorder
- semantic.color.brand.primary → colorPrimary

### 排版
- typography.fontFamily.primary → fontFamily
- typography.fontSize.base → fontSize
- typography.lineHeight.normal → lineHeight

### 圆角与边框
- component 中的 radius → borderRadius

### 阴影
- semantic.shadow → boxShadow

## 组件级覆盖
仅在以下条件允许：
- 语义 Token 无法满足 antd 组件需求
- 必须写明原因与来源

## 严格禁止
- 直接使用 antd 默认主题值
- 在组件中覆盖主题样式
