# 入职助手 · 员工使用端 Demo

新员工视角的入职助手**单页交互 Demo**：选择「模拟员工」卡片 → 用自然语言提问（门禁怎么办、电脑找谁领、请假制度怎么规定）→ 以 **SSE 流式**逐步展示 Planner 计划、每一步能力调用的输入输出、合规风控与最终回复（含引用可点开原文）。

> 本仓库只包含**员工端页面**（`employee.html`）。完整的 Plan + Skill/Tool 执行平台（后端引擎、知识库、评测、运营日志）在另一个仓库：
> **onboarding-assistant** —— https://github.com/shy122122/onboarding-assistant
> （Gitee 镜像：https://gitee.com/song-haiyan123/onboarding-assistant）

---

## 与其他部分的关系

```
onboarding-assistant/          # 完整平台（FastAPI 后端 + 管理端）
└─ app.py                      #   /emp 路由从同级目录 onboarding-demo/ 读取本页
onboarding-demo/
└─ employee.html               # 员工端页面（本仓库）
```

后端 `app.py` 通过 `/emp` 路由直接读取本页，因此两个目录**需保持同级**：

```
<任意父目录>\
├─ onboarding-assistant\
└─ onboarding-demo\
```

---

## 运行

```bash
# 1) 先启动后端（见 onboarding-assistant 仓库说明）
#    默认监听 http://127.0.0.1:8010

# 2) 用后端的 /emp 路由访问本页（推荐，可直连真实引擎）
#    浏览器打开 http://127.0.0.1:8010/emp
```

> **不要**直接以 `file://` 方式双击打开 `employee.html`：该页需要调用后端 `/api/employees`、`/api/run` 接口，`file://` 协议下无法连接，页面会显示连接失败提示。

---

## 页面能力

- **员工卡选择** —— 切换不同模拟员工（跨部门、不同入职阶段），会话按员工隔离。
- **自然语言提问** —— 输入框支持 Enter 发送、Shift+Enter 换行、自适应高度。
- **执行过程可见** —— 以事件流逐步渲染：Planner 计划 → 每步输入输出 → 风控卡 → 最终回复。
- **引用可核对** —— 回复中的 `[k]` 引用可点击定位，并展开原文摘录。
- **状态提示** —— 顶栏显示当前引擎状态（Live / Mock 自动）与后端连通性。

---

## 说明

- 本项目为个人独立完成，属「AI 企业入职助手」作品的员工端页面部分。
- 全部为本地模拟数据与演示账号，不含任何真实员工信息。
