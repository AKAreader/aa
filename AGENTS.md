# 工程协作规则

project_id: PRJ-IRSIM-001
mainline_version: 1.2

## 必须先读

每次制定、修改或执行任务，依次读取：
1. 本文件；
2. PRJ_IRSIM_001_MAINLINE.md；
3. PRJ_IRSIM_001_STATE.md；
4. docs/任务发布前审核规则.md；
5. 当前任务书及对应审核记录；
6. 本地工程 AGENTS.md、PROJECT_STATE.json 和实际输入证据。

不得从聊天记忆直接派工。记录读取的仓库 commit 与本地状态 revision。发生冲突时暂停受影响部分，保留双方记录并先核对。

## 状态真源和项目关系

本仓库存稳定主线、任务、设计审查和执行状态摘要。本地 PROJECT_STATE.json 是数值工程执行状态真源，不能复制伪造第二份，也不能因 GitHub 文档更新而自动提升 revision 或验收等级。

数值工程：D:\AgentOS\Projects\2026-09-26-多尺度热红外仿真数据研究
资产库：D:\Research\UAV_ASSET_LIBRARY
相关独立试点：D:\AgentOS\Projects\PRJ-COLLABPILOT-001，关系 other，不是数值工程。

历史聊天、其他 AI 的交接稿和厂商/项目技术方案均须标明来源及证据层级。方案拟选参数不等于实机测量，项目内传感器 ID 不等于厂商型号，文件能够打开不等于拥有公开发布许可。

## 每个任务发布前都审核

无论任务大小，每次发布及实质修改都需四方向审核：几何/可见光资产、飞行动作/可动结构、热学/红外成像、工程/数据科学。规则详见 docs/任务发布前审核规则.md。

审核必须绑定 task_id、task_version、mainline_version 及任务正文版本。写出问题、修改、未决项和放行范围。不相关方向写出不适用的理由，不省略审核。

单一助手从四个视角审查，必须标为 SINGLE_ASSISTANT_FOUR_PERSPECTIVE_DESIGN_REVIEW；顺序自审不是四个独立代理验收。设计放行不等于代码测试、物理验证或实机标定通过。

任务范围、参数、接口或验收标准实质变化后，旧审核失效；先复审再续跑。

## 每个任务必须声明

task_id / task_version / 中文名称 / mainline_version / requirement_ids / milestone / inputs / allowed_write_paths / protected_paths / acceptance_tests / resource_budget / non_goals / failure_policy / evidence_outputs / review_id。

公共脚本、全局索引和执行状态只由集成负责人写入。子会话使用独立写入目录，禁止并发修改同一 blend、公共配置或总数据库。

## 不可突破的边界

- 不用灰度着色、Emission 或伪彩代替数值红外链；在旧链旁建立版本化扩展，不破坏冻结基线。
- 原始资产、原始视频、许可、冻结清单、历史失败和源哈希保留。
- 不能把下载、导入、漂亮渲染、动画或配对成功当成物理真实性。
- 未知值使用 UNKNOWN；参数假设使用 ASSUMED；方案参数使用 SOURCE_DOCUMENT；导出计算使用 DERIVED；本机测量使用 MEASURED_THIS_UNIT。
- G0 来源合同、G2 标定、G4 独立验证不自动通过。未标定参数化仿真可以按获批任务推进，不等于已获得实机数字孪生。
- 不静默改变坐标、单位、标签、数据划分、门槛、相机响应或热物性。
- 本项目服务长期科研；未经另行授权，不改反无人机比赛分类器。

## 中文命名

所有新增用户可见阶段、任务、报告、Markdown 文件使用中文名称。内部 ID 和必要机器字段保留。AGENTS.md、既有主线/状态入口、软件固定文件名不强制重命名；不得批量破坏历史链接。

## 公开仓库保护

本仓库当前公开。只提交获准公开的方法、治理、任务和脱敏摘要。设备技术方案原文、详参、实拍、许可证受限模型、个人路径清单和未发布实验数据默认留本地。上传前用明确文件白名单核对，不使用未经检查的全量提交。不擅自改变仓库可见性。

## 完成纪律

按证据分别给出 PASS / PASS_WITH_LIMITATIONS / FAIL / BLOCKED / NOT_RUN。几何、运动、热学、成像、标定、真实验证、许可分别判定。

完成后先执行任务后验收，附命令、配置、日志、哈希与失败记录；有授权才更新本地状态，GitHub 摘要注明证据来源。到授权边界停止，不自动扩量。仅主线变化时升级主线版本。
