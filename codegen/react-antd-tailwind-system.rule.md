---
alwaysApply: true
---

# 规则：AI 生成 React + TypeScript + antd v5 + TailwindCSS v4 的系统规范

## 适用环境

- React 19
- TypeScript
- antd v5（统一主题与视觉系统）
- TailwindCSS v4（仅用于布局原子类）
- 项目存在自定义 antd Design Tokens

---

## 一、AI 的核心职责

你的目标是：

- 生成 **100% 可运行、结构清晰、可维护** 的前端代码
- 严格遵守团队工程规范
- 不修改未被明确要求修改的文件
- 根据 DSL 自动生成 UI 结构
- 所有视觉样式交由 antd 主题系统处理
- Tailwind 仅用于布局，不参与视觉设计
- 不写死任何视觉相关常量（颜色 / 字体 / 阴影 / 圆角）

---

## 二、TailwindCSS 使用限制（强制约束）

### ❌ 严禁使用的 Tailwind 类

禁止出现任何**视觉相关**类，包括但不限于：

- 颜色类  
  `text-red-500` / `bg-blue-100` / `text-[var(--xxx)]`

- 字体类  
  `text-sm` / `text-xl` / `font-bold`

- 圆角类  
  `rounded` / `rounded-lg`

- 阴影类  
  `shadow-sm` / `shadow-md`

- 任意颜色插值  
  `text-[#333]` / `bg-[rgb(0,0,0)]`

> 原因：所有视觉表现必须由 antd token 控制，而不是 Tailwind。

---

## 三、TailwindCSS 白名单（仅允许以下类别）

### ✅ 布局

- `flex` / `inline-flex` / `grid`
- `flex-col` / `flex-row`
- `items-*` / `justify-*`
- `gap-*` / `space-*`
- `grid-cols-*` / `grid-rows-*`

### ✅ 间距

- `p-*` / `px-*` / `py-*`
- `m-*` / `mx-*` / `my-*`

### ✅ 定位

- `relative` / `absolute`
- `top-*` / `left-*` / `right-*` / `bottom-*`

### ✅ 尺寸

- `w-*` / `h-*`
- `min-w-*` / `max-w-*`
- `aspect-video`

### ✅ 排版辅助（非视觉）

- `text-left` / `text-center` / `text-right`
- `truncate` / `line-clamp-*`
- `leading-*` / `tracking-*`

> 白名单之外的 Tailwind 类一律禁止。

---

## 四、视觉样式的唯一来源：antd Token

所有视觉相关属性 **必须** 使用 antd 的 token API：

```ts
const { token } = theme.useToken();

包括但不限于：

颜色
token.colorText
token.colorTextSecondary
token.colorPrimary
token.colorBgContainer
token.colorBorder

字体
token.fontSize
token.fontSizeLG
token.fontWeightStrong
token.lineHeight

阴影
token.boxShadow
token.boxShadowSecondary

圆角
token.borderRadius
token.borderRadiusLG

示例（推荐写法）
<Paragraph style={{ color: token.colorTextSecondary }}>
  {subtext}
</Paragraph>

五、组件优先级规则

在可行的情况下，必须优先使用 antd 组件：

Typography

Layout

Card

Button

Form / Input

Tabs

Table

Row / Col

Carousel

Space

避免手写 HTML 承载视觉与结构。

六、代码结构规范

仅使用 React 函数组件

使用 TypeScript

Props 必须声明 interface

组件职责清晰（页面 / UI / Hook）

常量与配置抽离至顶部

不做用户未要求的重构或优化

七、DSL 解析与生成策略

根据 DSL 的 section / block 结构生成页面

使用 antd 组件 + Tailwind 布局组合

视觉全部来自 antd token

DSL 缺失字段可合理推断，但不得越权设计

八、代码生成优先级

生成代码时，遵循以下优先级顺序：

功能与结构正确

可维护性与可读性

严格遵守 antd Token 体系

Tailwind 仅用于布局

代码可直接运行

组件拆分合理

九、严格禁止行为

自动重构或删除未提及代码

使用 Tailwind 替代 antd 进行视觉设计

写死任何视觉相关值

使用 Tailwind 黑名单类

覆盖全局 CSS

生成不可运行代码

