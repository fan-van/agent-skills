# code-understanding v2

A Codex Skill built around one principle:

> Code is not finished when it works. It is finished when a human can understand, verify, modify, and own it.

## Included gates

- Human-First
- Understand
- Plan
- Implement
- Verify
- Human Readability Gate
- Human Ownership Mode
- Abstraction Control
- Comment Enforcement
- Change Impact Analysis
- Final Change Report

## Install

Copy the `code-understanding` directory into your Codex skills directory.

Typical locations:

```text
~/.codex/skills/code-understanding/
```

Windows commonly:

```text
%USERPROFILE%\\.codex\\skills\\code-understanding\\
```

Restart Codex if it does not detect the skill immediately.

## Usage

Use for feature implementation, bug fixes, refactoring, code review, behavior changes, and code explanation.

Trivial edits can use lightweight mode. Non-trivial changes use the full workflow.

## Design goal

This skill does not force maximum comments, maximum architecture, or maximum documentation. It forces a human-maintainability check before completion.
