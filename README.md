# 加油订单详情页 UI Skill 项目

这个项目用于沉淀「加油订单详情页」的 Design Skill，让 AI 可以根据 Figma 截图或源文件，高还原生成移动端页面、HTML/CSS、React 组件或可继续编辑的 UI 稿。

## 项目目标

1. 固定加油订单详情页的信息结构和视觉规则
2. 让 AI 输出时保持高还原度
3. 统一颜色、字体、间距、卡片、金额明细、底部操作栏等规则
4. 方便后续接入 Cursor / Codex / GitHub / 前端项目

## 推荐使用方式

1. 把原始截图放入 `references/original-screenshot.png`
2. 把 Figma 链接写入 `figma/figma-link.txt`
3. 让 AI 先阅读 `design-skill.md`
4. 再让 AI 根据截图或 Figma 生成页面到 `output/`
5. 每次修改后，在 GitHub Desktop 里 Commit 保存版本

## 文件结构

```text
gas-order-ui-skill/
├─ README.md
├─ design-skill.md
├─ prompt.md
├─ figma/
│  └─ figma-link.txt
├─ references/
│  └─ original-screenshot.png
├─ assets/
│  ├─ images/
│  └─ icons/
├─ output/
│  ├─ preview.html
│  └─ style.css
└─ notes/
   ├─ review-checklist.md
   └─ changelog.md
```

## 当前版本

v1.0：基础 Design Skill 项目结构。
