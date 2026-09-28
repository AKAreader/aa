# AGENTS.md

## Project

project_id: `PRJ-IRSIM-001`

This repository is the persistent governance source for the low-altitude UAV visible/infrared simulation program.

## Mandatory read order

Before proposing, modifying, or executing any Codex task, read:

1. `PRJ_IRSIM_001_MAINLINE.md`
2. `PRJ_IRSIM_001_STATE.md`
3. Any task-specific file referenced by the current state

Do not plan from conversational memory alone.

## Single-source rules

- `PRJ_IRSIM_001_MAINLINE.md` is the authoritative project direction and acceptance philosophy.
- `PRJ_IRSIM_001_STATE.md` is the latest governance snapshot and may change frequently.
- The local project's own `PROJECT_STATE.json` remains the execution-state source of truth for the numerical IR project.
- Historical reports, chats and screenshots are evidence inputs, not automatic current truth.
- If GitHub governance and local `PROJECT_STATE.json` conflict, stop the affected task, record the conflict, and reconcile before continuing.

## Local project links

Numerical IR project root:

`D:\AgentOS\Projects\2026-09-26-多尺度热红外仿真数据研究`

UAV asset library root:

`D:\Research\UAV_ASSET_LIBRARY`

Related but distinct collaboration pilot:

`D:\AgentOS\Projects\PRJ-COLLABPILOT-001`

Do not confuse that pilot with the numerical IR project.

## Non-negotiable boundaries

- Do not replace the existing numerical IR chain with Blender emission, grayscale shading, pseudocolor, or an unvalidated substitute.
- Do not treat source download, Blender import, attractive rendering, animation, or synthetic image appearance as proof of physical validity.
- Preserve original assets, hashes, historical failures, license records and frozen baselines.
- Unknown values remain `UNKNOWN`, `ASSUMED`, `UNCALIBRATED`, `BLOCKED`, or `NOT_RUN`; never fabricate values to complete a table.
- Do not silently change evaluation gates, source grouping, label policy, camera assumptions, thermal parameters, or geometry confidence.
- Do not modify the anti-UAV competition classifier repository as part of this simulation program unless the user explicitly authorizes a separate task.

## Task governance

Every execution task must declare:

- task_id
- mainline_version
- requirement_ids
- milestone
- inputs
- allowed_write_paths
- protected_paths
- acceptance_tests
- non_goals
- failure_policy
- evidence_outputs

Work without a mapped requirement or milestone does not enter the execution queue.

Major changes to:
- project objective
- fidelity definition
- toolchain
- data contract
- coordinate convention
- directory migration
- acceptance gates
- calibration strategy

require a four-direction review before adoption:

1. Geometry / visual asset
2. Motion / flight / articulations
3. Thermal / radiometry / IR imaging
4. Software engineering / data / validation

## Status vocabulary

Use evidence-backed statuses such as:

`PASS`
`PASS_WITH_LIMITATIONS`
`FAIL`
`BLOCKED`
`NOT_RUN`
`UNCALIBRATED`
`GEOMETRY_PARTIAL`
`REFERENCE_ONLY`

Do not compress multiple dimensions into a single vague `READY`.

## Completion discipline

At the end of each substantial task:

1. compare results against the current mainline;
2. update the local project's state if authorized;
3. update `PRJ_IRSIM_001_STATE.md` in this repository with a concise snapshot;
4. update the mainline only when the project direction or acceptance philosophy changes;
5. stop at the authorized milestone and do not auto-expand scope.


## 中文命名规则

从现在起，所有面向用户的新阶段、新任务、新验收报告和新建 Markdown 文件，统一使用中文名称。

内部追踪编号（如 `P2-001`、`M4`、`G2`、`G4`）继续保留，但仅用于：
- 元数据；
- 状态追踪；
- 验收映射；
- 括号内辅助说明。

不得再把英文缩写或内部编号作为主要阶段名、任务标题或新建文件名。

推荐格式：
- 阶段名：`真实设备与真实数据合同审计阶段`
- 任务文件：`tasks/真实设备与真实数据合同审计.md`
- 内部元数据：`task_id: P2-001`

历史文件不强制批量重命名，以免破坏引用；从本规则生效后的新任务开始执行中文命名。
