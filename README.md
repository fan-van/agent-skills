# 个人 Agent Skills

## 按任务查找

| 分类 | 技能 | 什么时候用 |
| --- | --- | --- |
| 源码学习 | [代码与数据流讲解](explain-code-data-flow/SKILL.md) | 想看懂一段现有代码时，从一笔业务数据出发，跟到函数调用、数据库读写和页面结果。 |
| 开发与验收 | [代码修改与验收](code-understanding-v2/SKILL.md) | 要实现功能、修 bug 或审查改动时，核对影响范围、可读性和验证证据。 |
| 故障排查 | [报错说明](explain-errors-as-they-happen/SKILL.md) | 任务执行中出错，或收到失败日志时，先解释哪里停了、证据说明了什么、影响到谁，再继续排查并报告结果。 |

## 让报错说明默认生效

将 `explain-errors-as-they-happen` 整个目录复制到个人 Codex 的 `~/.codex/skills/`。要将它设为长期偏好，可把下面这段加到个人 `~/.codex/AGENTS.md` 中。

> 工作中遇到报错，或我贴回失败日志、截图时，主动读取并应用 `~/.codex/skills/explain-errors-as-they-happen/SKILL.md`。先讲清哪一步停了、日志证明了什么、实际影响和下一步。原因尚未查明时先报告已知事实，查明后补充。连续报错按发生顺序解释。
