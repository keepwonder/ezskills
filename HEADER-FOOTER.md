# Header / Footer · EzSkills

> 综合规范：[../../SITE-CONSISTENCY.md](../docs/rules/SITE-CONSISTENCY.md)
> 状态：✅ 已对齐（2026-10-18）

## Header

- 全宽 `sticky top:0`，`--container: 984px` + 32px 内边距；桌面 64px。
- 品牌纯文字 `EzSkills` + 英文副标；中间搜索框；右侧主题 / 添加技能。
- ≤720px 折成两行：品牌 + 动作一行，搜索框第二行（有意例外）。

## Footer

- 全宽 top-border；纯文字 `EzSkills` + 「数据仅保存在本机浏览器，建议定期导出备份」。
- 数据操作：导出 JSON / 导入 / 恢复示例。
- 链接行：**主站 ↗** / GitHub ↗ / Skills.sh ↗ / ClawHub ↗ + © 2026 Kiang。
- 与 Header 无重复导航。

## 主题

- `data-theme` + `localStorage["kiang-theme"]`；兼容旧 `ezskills.theme`，不会丢偏好。
- 首屏 inline script 防闪白。

## 关键文件

- `ezskills/index.html`：Header / Footer / 主题逻辑均内联。
- 卡片网格 `minmax(280px, 1fr)`：984 容器下仍保持 3 列。

## 验证

```bash
cd ezskills && python3 -m http.server 8766
# 检查：984 容器、3 列卡片、Footer 主站入口、旧主题键迁移、主题切换
```
