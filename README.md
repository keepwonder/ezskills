# EzSkills

个人技能库：把 AI 编程、前端、后端、工具、内容、设计六大类技能收在一张表里，记录学习状态、进度与使用次数。

- 线上：<https://ezskills.kiang.website/>
- 形态：单文件静态页，零依赖、零构建、零后端
- 数据：只存在浏览器 `localStorage`，支持 JSON 导出 / 导入

## 文件

```
index.html   # 唯一入口：内联 CSS / JS，无外部请求
```

没有 `package.json`、没有构建步骤。修改后用任意静态服务器预览即可：

```bash
python3 -m http.server 8765
# http://127.0.0.1:8765/
```

## 数据模型

localStorage 键：`ezskills.data.v2`

```json
{
  "version": 2,
  "updatedAt": "2026-10-18T12:00:00.000Z",
  "skills": [
    {
      "id": "1",
      "name": "find-skills",
      "category": "tools",
      "source": "skills.sh",
      "url": "https://skills.sh",
      "desc": "发现并安装新的 Agent Skills",
      "tags": ["skills", "discovery"],
      "status": "mastered",
      "progress": 100,
      "uses": 42,
      "icon": "🔍",
      "createdAt": "2026-10-18T12:00:00.000Z"
    }
  ]
}
```

- `category`：`ai-coding` / `frontend` / `backend` / `tools` / `content` / `design`
- `status`：`not-started` / `learning` / `mastered`
- 旧键 `ezskills_data`（数组）会在首次加载时自动迁移到 v2，迁移成功后删除旧键。

默认的 12 条示例数据写在 `index.html` 的 `DEFAULT_SKILLS` 常量里。

## 功能

- 分类、标签、关键词筛选（关键词覆盖名称 / 描述 / 标签 / 来源）
- 技能详情：状态切换、`+1 使用`、编辑、删除（可撤销）
- 添加 / 编辑表单，URL 仅接受 `http(s)`
- 导出 JSON、导入 JSON（覆盖前二次确认）、恢复示例数据
- 深浅色主题：跟随系统，可手动切换并记忆
- 键盘：`/` 聚焦搜索，`Esc` 关闭弹窗，卡片支持 Enter / Space 打开

## 设计系统

沿用 Kiang 视觉系统：暖纸底 `#f7f2e8` + 墨色 `#151713` + 翡翠绿 `#047a55`，Georgia 标题 / Avenir 正文 / SF Mono 数据。深色模式切到 `#12140f`。所有样式内联在 `index.html`，不加载 Tailwind CDN 或外部字体。

## 部署

- GitHub：`keepwonder/ezskills`（`main`）
- Vercel：项目 `ezskills`，Git Integration 自动部署
- 域名：`ezskills.kiang.website` → Vercel（Cloudflare DNS-only CNAME）

**push 到 `main` 即产线部署。** 推完用 `curl https://ezskills.kiang.website/` 或 Vercel API 确认 `READY`。

## 维护提示

- 改主页项目卡片的描述 / 技术栈，要同步更新 `kiang-website` 仓库的 `site/projects.json`。
- 线上截图资产在主站 `site/assets/projects/ezskills/desktop/hero.webp`，改版后需要重拍。
