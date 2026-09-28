# PRJ-IRSIM-001｜当前状态快照

snapshot_date: **2026-09-28**  
mainline_version: **1.1**  
local_project_state_revision: **55**  
governance_status: **ACTIVE**

---

## 1. 关键路径

### 数值 IR 项目根目录

`D:\AgentOS\Projects\2026-09-26-多尺度热红外仿真数据研究`

### UAV 资产库

`D:\Research\UAV_ASSET_LIBRARY`

### 相关但独立的协作试点

`D:\AgentOS\Projects\PRJ-COLLABPILOT-001`

关系：`other`。不得再把它作为目标数值 IR 工程。

---

## 2. P1-001 / P1-001-R1 状态

formal_acceptance: **ACCEPTED_WITH_LIMITATIONS**  
acceptance_scope: **M4 受限单机诊断验收；未进入 G2/G4；未启动 M5**  
acceptance_basis: **R4 强哈希匹配、631/631 清单一致、G1/R4 回归通过、12/12 RGB/IR 同步与标签核验通过**


总体：

`PASS_WITH_LIMITATIONS`

M4：

`PASS_WITH_LIMITATIONS / UNCALIBRATED`

本阶段已经停止扩量。

---

## 3. 原基线恢复结果

- 当前 `PROJECT_STATE.json` revision：55
- R4 路径：
  `D:\AgentOS\Projects\2026-09-26-多尺度热红外仿真数据研究\lanes\worker-physics\workspace\r4_scene_pilot`
- R4 `manifest.sha256` 文件 SHA-256：

`77925FC3EF95178C8B0CF780B90EF6F4F40088B84F5C0E17FD57B17220D7EDD6`

- `R4_MANIFEST_HASH_MATCH = TRUE`
- 清单内：631/631 一致
- `BASELINE_RECOVERED = TRUE`
- G1 tests：14/14 PASS
- R4 tests：9/9 PASS
- R4 frame structure：30/30 PASS
- G1 清单唯一现值差异：签收后追加工作日志；其余 27 项一致
- 旧 R4 的 9 个 `rejected` 保持原判

---

## 4. 当前生产资产样板

### Avata 2｜样板 A

当前已经具备：

- production master
- runtime copy
- 四个独立旋翼轴
- 运动诊断工程
- 共同状态缓存
- 热网络接口
- 已接入原 R4 几何接口
- 原数值 IR 模块未替换
- 热网络同钟 `body_shell` 温度已进入 UAV 材料口

当前限制：

- 旋翼真实旋向未实测/未校准
- RPM /真实飞控关系未标定
- 热参数未标定
- 相机未标定
- 当前 IR 仍使用均匀机体表面温度映射

运动/热/IR 结论不得高于未标定诊断级。

### Air 3S｜样板 B

当前：

`GEOMETRY_PARTIAL`

已经建立可编辑的：

- 机身前部
- 传感器结构
- 双摄结构

当前多角度证据不足以可靠确定：

- 完整电机位置
- 完整机臂
- 桨/轴距几何

因此没有补猜，暂不进入 M4 主路径。

---

## 5. 当前资产库盘点

最新已核验阶段记录：

- 13 份三维源文件
- 覆盖 11 款 DJI
- 7 份比例待核原样导入工程
- 原始源文件和导入工程哈希未因 P1 改动
- 非 DJI 五类资料任务为旁路工作，必须继续服从主线与资产标准

这些数量是当前项目快照，不写入永久主线。

---

## 6. M4 受限诊断结果

Avata 2 已进入原数值 IR 主链。

本轮产生：

- 12 组 RGB/IR 配对样本
- 10 positive
- 1 negative
- 1 ignore
- 12/12 同步与标签核验通过

本轮结论仅为：

`UNCALIBRATED_END_TO_END_INTEGRATION`

不代表：

- 真实相机匹配
- 热物理准确
- 可直接替代实拍
- 已通过 G2/G4
- 已可扩展 M5 大规模生产

---

## 7. 仍未通过/未标定

### G0 / 数据合同

仍需确认或完善真实样本的：

- 来源
- 使用授权
- 相机/镜头
- 波段
- 原始位深
- NUC/AGC
- 温度映射
- 目标标注
- 采集组
- 真实独立留出定义

### G2 / 设备标定

仍未完成：

- 真实相机光谱响应
- 曝光/积分时间
- 光学/PSF
- 噪声
- 黑体/均匀场
- NUC 相关行为
- 时序稳定性
- 可追溯独立标定会话

### 目标热物理

仍未标定：

- 材料发射率
- 热容
- 导热
- 对流
- 环境边界
- 分部件实际温度历史
- 电机/ESC/电池等真实损耗和热传递

### G4 / 真实独立验证

未完成：

- 封存独立实拍组
- 真实/合成同输出阶段比较
- 预登记误差
- 下游检测/识别盲测

---

## 8. 当前里程碑状态

| Milestone | Status |
| --- | --- |
| M0 事实/治理/接口 | PASS_WITH_LIMITATIONS |
| M1 生产资产 | IN_PROGRESS |
| M2 运动执行 | UNCALIBRATED_DIAGNOSTIC |
| M3 热状态 | UNCALIBRATED_DIAGNOSTIC |
| M4 双波段采集 | PASS_WITH_LIMITATIONS / UNCALIBRATED |
| M5 场景与扩量 | NOT_STARTED |
| M6 真实验证 | BLOCKED_BY_G2_G4 |

---

## 9. 当前唯一优先主任务

在启动 M5 批量场景与数据扩量之前，优先取得并核验：

1. 真实热像设备参数；
2. 独立实拍留出的来源、采集组和授权；
3. 可用于 G2 的标定资料；
4. 可用于 G4 的封存真实对照。

这些证据到位后，才决定：
- 先修正相机链；
- 先修正热模型；
- 还是进入更复杂场景扩展。

---

## 10. 后续任务前必读

任何新 Codex 任务必须按以下顺序读取：

1. `AGENTS.md`
2. `PRJ_IRSIM_001_MAINLINE.md`
3. 本文件
4. 本地 `PROJECT_STATE.json`
5. 任务所需的实际报告/资产/代码

不得只依据上一轮聊天摘要继续执行。
