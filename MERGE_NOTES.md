# AgileCampus 合并说明

合并日期：2026-09-25

## 已合并栏目

- 基准项目：团队、项目、看板、时间线、计划中心、设置与 Agent API。
- Vivi 交付：资源中心、个人日历、成果中心、项目交付物审核。
- Task B：文档协作、评论、文档转任务、版本历史、交付审核演示。
- Task D：教师关注、消息、通知三个交互原型。

## 统一入口

- 登录后首页：/workspace
- 项目执行：/projects
- 计划中心：/plan
- 个人日历：/calendar
- 资源中心：/resources
- 文档与交付：/task-b
- 成果中心：/achievements
- 教师工作台：/prototype/teacher-focus

## 数据库变更

保留原计划中心的 research_projects 与 plan_tasks，并新增资源、预约、项目交付物和校外成果相关表。首次运行前请配置 .env，随后执行：

    npm install
    npm run db:push
    npm run db:merge
    npm run dev

## 验证结果

- npm run lint：0 个错误，保留原测试文件 1 条未使用变量 warning。
- npx tsc --noEmit：通过。
- npx next build --webpack：通过，共生成 30 个页面路由。
- /task-b、教师关注、消息、通知和登录页均返回 HTTP 200。

根布局已移除构建时在线下载 Google Fonts 的依赖，改用系统字体栈，离线环境也能构建。
