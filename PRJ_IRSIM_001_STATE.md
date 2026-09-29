# 当前状态快照

project_id: PRJ-IRSIM-001
mainline_version: 1.2
governance_update_date: 2026-09-29
last_reported_execution_snapshot_date: 2026-09-28
last_reported_local_revision: 55
execution_evidence: USER_REPORTED_AND_PREVIOUS_GOVERNANCE_SNAPSHOT；本轮未访问 Windows 或独立复跑。

## 一、执行目录与身份

数值工程：D:\AgentOS\Projects\2026-09-26-多尺度热红外仿真数据研究
资产库：D:\Research\UAV_ASSET_LIBRARY
相关独立试点：D:\AgentOS\Projects\PRJ-COLLABPILOT-001；关系 other，不是原数值工程。

原状态文件保持执行真源。本次治理文档更新不表示本地 revision 已增加。

## 二、保留的阶段状态

P1-001-R1：此前治理签收为 ACCEPTED_WITH_LIMITATIONS，范围仅 M4 受限单机诊断；UNCALIBRATED。签收依据来自用户提交的执行汇报，不能说本轮已独立重验。

R4 目录：数值工程/lanes/worker-physics/workspace/r4_scene_pilot。
报告的 manifest 文件 SHA256：77925FC3EF95178C8B0CF780B90EF6F4F40088B84F5C0E17FD57B17220D7EDD6。
报告的清单：631/631 一致；G1 14/14、R4 9/9、帧结构 30/30 通过。G1 唯一现值差异为签收后追加工作日志，其余 27 项一致。旧 R4 九个 rejected 不改判。

Avata 2：已有生产母版/运行副本、四旋翼轴、状态缓存、热网络和原链接入；当前 IR 仍使用均匀 body_shell 表面温度。旋向、RPM/负载、热物性、相机响应均未实测。

Air 3S：GEOMETRY_PARTIAL；机身前部、传感器和双摄可编辑；完整机臂、电机位置、桨/轴距缺证据，不补猜。

资产盘点快照：13 份源文件、11 款 DJI、7 份比例待核原始导入。非 DJI 旁路资料任务沿统一规范；数量需本地后续实查，不硬编码为验收指标。

已报告配对：12 组、10 positive/1 negative/1 ignore、12/12 同步标签通过；分辨率 64×64。它们证明既有受限接口联通，不证明实机匹配、分部件热场、全分辨率或数据集无泄漏。

## 三、本轮新增的是设计与参数证据，不是仿真结果

外部交接稿已逐节吸收；原技术方案相关章节已核对。详细设备参数和原文保留本地/用户会话，不进入公开仓库。

CAM01 作为来源化研究配置使用；方案拟选参数不确认交付实机，也不把旧视频绑定到该配置。原文冲突、未知 RAW/AGC/NUC/RSR/时序和具体设备身份继续保留。

主线 1.2 正式分开参数化仿真研发与具体设备标定；不以未取得全部实测资料为所有工程建设的阻塞，也不降低 G2/G4。

每次派工前审核已写入 AGENTS.md 和发布规则；本轮为单助手四视角桌面设计审查，不是四名独立执行者验收。

## 四、当前执行队列

next_task_id: P2-002
next_task_version: 1.0
next_task_name: 首台相机参数化成像与分部件热场联调
next_task_file: tasks/首台相机参数化成像与分部件热场联调.md
review_file: docs/外部交接材料吸收与四方向审核.md
next_task_status: APPROVED_WITH_GATES / NOT_EXECUTED_IN_THIS_CHAT

P2-001《真实设备与真实数据合同审计》保留为并行真实证据工作；尚未收到完成证据，不能宣布完成。其原“唯一优先”调度由当前主线修订，不删除旧任务和历史。

本轮下一任务范围：来源化相机配置、分部件表面热映射、旧链版本化适配、原生单帧和最多三十组短序列诊断、审计框架。资源/数值门不过则停止受影响部分。不得启动大规模数据或全机型制作。

## 五、里程碑状态未被治理发布提升

| 里程碑 | 当前执行证据状态 |
| --- | --- |
| M0 事实/治理/接口 | PASS_WITH_LIMITATIONS；新规则待本地接入 |
| M1 生产资产 | IN_PROGRESS |
| M2 运动 | UNCALIBRATED_DIAGNOSTIC |
| M3 热状态 | UNCALIBRATED_DIAGNOSTIC；分部件成像待做 |
| M4 双波段 | 既有受限 PASS_WITH_LIMITATIONS；新相机原生诊断未运行 |
| M5 场景/扩量 | 未启动批量生产 |
| M6 真实验证 | G2/G4 证据未完成 |

## 六、持续未决

G0：真实来源、权限、相机实例/镜头、原始输出阶段、采集组及设备关联。
G2：本机响应、光学、时序、噪声、NUC、可追溯标定与独立会话。
目标热学：发射率、热容/导热/对流、损耗、环境与分部件表面温度历史。
G4：独立实拍留出、使用历史、同阶段比较和预登记评估。

真实留出及其使用历史应现在规划，不等仿真全部做完再寻找“从未见过”的数据。只有处理后视频也能作为原始采集保留，但不能反推未提供的高位深 RAW。

## 七、下一次接管

读 AGENTS.md -> 主线 -> 本状态 -> 发布规则 -> 当前任务和审核 -> 本地执行状态及证据。核对治理 commit 与任务版本再执行；实质变更必须复审。
