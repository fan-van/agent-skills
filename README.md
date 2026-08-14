# agent-skills (worktree session)

本工作区为 Copilot CLI 创建的会话 worktree，用于在独立分支上进行实验性改动而不影响主 checkout。

快速说明：

- 主 checkout（canonical working copy）：
  C:\Users\fwg\develop\agent-skills
  用于长期开发、运行与调试。

- 会话 worktree（隔离实验）：
  C:\Users\fwg\develop\copilot-worktrees\agent-skills\fan-van-super-adventure
  在此路径上创建/编辑、提交并推送到远端分支（示例：fan-van-super-adventure）。

推荐工作流（安全、可审查）：
1. 在 worktree 上创建分支、做改动并提交(push)。
2. 在 GitHub 上通过 Pull Request 审查并合并到 main。合并后在主 checkout 执行 `git pull` 同步。

其他文件说明：
- 会话 artifacts（图示 HTML）：
  %USERPROFILE%\.copilot\session-state\<session-id>\files\git-workflow.html
  %USERPROFILE%\.copilot\session-state\<session-id>\files\directory-layout.html

提交规范：请在提交消息末尾保留 Co-authored-by: Copilot App <223556219+Copilot@users.noreply.github.com>

如需我在主 checkout 直接工作或切换会话类型，请说明。