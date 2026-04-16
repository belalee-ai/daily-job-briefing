# Daily Job Briefing / 每日职位更新简报

一个 Claude Skill，帮你每天自动搜索目标城市、目标行业的最新招聘信息，输出一份包含岗位推荐、薪资分析、市场趋势和行动清单的求职日报。

## 功能亮点

- **个性化匹配**：首次使用时了解你的背景（城市/行业/岗位/薪资/偏好），后续所有推荐基于你的画像定制
- **三层信源**：公司官方招聘页 → 招聘平台(BOSS直聘/猎聘) + LinkedIn → 行业媒体，按可信度分级
- **四维评分**：经验匹配(35%) + 薪资竞争力(25%) + 成长潜力(20%) + 求职因素匹配(20%)
- **6种模式**：完整日报 / 快速日报 / 定向追踪 / 历史回看 / 标记追踪 / 市场概览
- **标记系统**：对话中说"标记XX"即可持续关注某岗位，支持智能衰减和自动归档
- **多行业覆盖**：预置 AI、互联网、金融科技、游戏、新能源、电商 6 大行业的公司清单和搜索模板

## 安装

```bash
git clone https://github.com/belalee-ai/daily-job-briefing.git ~/.claude/skills/daily-job-briefing
```

## 使用方式

安装后在 Claude 中使用以下触发词：

| 说法 | 效果 |
|------|------|
| "职位日报" / "今天有什么新岗位" | 生成完整日报 |
| "快速日报" / "简版" | 只看第一梯队的精简版 |
| "字节有更新吗" | 定向追踪某家公司 |
| "我标记的" / "追踪进展" | 查看所有标记岗位的最新动态 |
| "市场行情" / "薪资趋势" | 专项市场分析 |
| "更新我的信息" | 修改目标城市/行业/薪资等偏好 |

首次使用时会引导你完成 6 个问题的快速设置（约 2 分钟）。

## 目录结构

```
daily-job-briefing/
├── SKILL.md                              # 核心指令文件
├── LICENSE.txt                           # MIT License
├── README.md                             # 本文件
├── templates/
│   ├── daily-job-report.md               # 日报输出模板
│   └── user-profile-template.md          # 用户画像模板
├── shared/                               # 运行时数据（自动生成，已 gitignore）
│   ├── user-profile.md                   # 用户画像（首次设置后生成）
│   ├── bookmarks.md                      # 标记追踪清单（使用后生成）
│   ├── report-index.md                   # 日报索引导航（自动维护）
│   ├── reports/                          # 日报输出文件
│   └── resume/                           # 简历文件（可选，用户自行放置）
└── references/
    └── search-sources.md                 # 各行业搜索信源和关键词模板
```

## 可选增强

- **简历匹配**：将简历放入 `shared/resume/` 目录，日报会引用你的具体项目数据做匹配分析
- **Web Access Skill**：安装 [web-access](https://github.com/eze-is/web-access) 可解锁浏览器抓取、登录态访问等增强搜索能力

## 数据与隐私

本 skill 在运行时会在 `shared/` 目录下创建以下本地文件：

- `user-profile.md` — 你的求职画像（目标城市、行业、岗位、薪资期望等）
- `bookmarks.md` — 你标记关注的岗位清单
- `resume/` — 你自行放置的简历文件
- `reports/` — 生成的日报文件

**所有数据仅存储在你的本机**，不会上传到任何服务器。上述文件已在 `.gitignore` 中排除，不会被 git 提交。如果你 fork 或分享本仓库，请确认 `shared/` 目录下无个人数据。

## License

MIT
