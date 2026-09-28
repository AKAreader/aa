# P2-001｜G2/G4 输入审计与真实设备/真实数据合同冻结

task_id: **P2-001**  
project_id: **PRJ-IRSIM-001**  
mainline_version: **1.1**  
milestones: **G0/G2/G4 输入准备；不启动 M5**  
status: **AUTHORIZED_NEXT_TASK**

---

## 1. 任务目标

在不修改既有数值 IR 主链、不扩量、不新增复杂场景的前提下，查清并冻结：

1. 当前真实热像设备究竟是什么；
2. 现有真实视频/图像的来源、授权、采集组和设备关联；
3. 哪些参数可以从官方资料、原始文件、元数据或实验记录直接确认；
4. 哪些参数必须通过实测标定获得；
5. 哪些真实数据可以合法且科学地作为 G4 独立留出；
6. G2/G4 下一步需要怎样的最小测量计划。

本任务不是“做标定结果”，而是先完成**标定输入合同和真实数据合同的证据审计**。

---

## 2. 必读顺序

开始前必须读取：

1. `AGENTS.md`
2. `PRJ_IRSIM_001_MAINLINE.md`
3. `PRJ_IRSIM_001_STATE.md`
4. 本地：
   `D:\AgentOS\Projects\2026-09-26-多尺度热红外仿真数据研究\PROJECT_STATE.json`
5. G0/R0/R2/R3/G1/R4 已有报告
6. P1-001-R1 验收产物与项目链接

不得仅依据聊天摘要执行。

---

## 3. 四方向审查约束

### A. 几何 / RGB 资产

本轮 Avata 2 和 Air 3S 不继续扩结构。

允许：
- 读取现有 asset_id / version / geometry status；
- 确认真实数据中能否辨认机型/姿态/距离等校准关联字段。

禁止：
- 为了 G2/G4 新做更多无人机；
- 修改 Avata 2 生产几何；
- 补猜 Air 3S 未知结构。

### B. 运动 / 飞行

本轮不升级飞行模型。

允许：
- 记录真实数据可获得的轨迹、距离、高度、速度、姿态、飞行阶段；
- 判断哪些量可作为后续飞行/热模型约束。

禁止：
- 将现有 `KINEMATIC_CONSTRAINED` 升级为动力学验证；
- 编造真实 RPM、旋向或飞控参数。

### C. 热学 / 辐射 / IR

这是本轮主方向。

必须区分：
- 官方规格可确认；
- 文件/元数据可确认；
- 现有实验记录可确认；
- 必须实测；
- 当前不可得。

不得把官方 datasheet 中的典型值自动当成本机实测值。

### D. 软件工程 / 数据 / 验收

建立可追溯的设备、数据、标定输入合同。

任何“真实独立留出”必须证明它没有进入仿真参数拟合、阈值选择、噪声拟合、热参数调参或后续模型选择。

---

## 4. 先审计当前真实数据

从既有 G0/R0 记录和本地文件中核验目前真实 MP4/MAT/图像。

对每个真实源建立 source record：

- source_id
- absolute_path
- SHA256
- file type
- resolution
- frame rate
- bit depth（若能确认）
- codec / container
- visible stored range
- capture date（若可确认）
- camera model（若可确认）
- lens（若可确认）
- spectral band（若可确认）
- NUC/AGC mode（若可确认）
- temperature/radiometric mapping（若可确认）
- target class / model（若可确认）
- distance/range evidence
- flight/capture session
- provider
- license/authorization evidence
- parent capture group
- prior project usage

未知字段写 `UNKNOWN`。

---

## 5. 识别真实热像设备

优先从：

- 文件元数据；
- 原始文件名与 sidecar；
- MAT 内容；
- 采集说明；
- 项目日志；
- 用户手册/设备清单；
- 已有比赛/科研资料；
- 设备照片（如本地存在且与数据明确关联）

寻找设备身份。

输出：

`REAL_CAMERA_IDENTITY_AUDIT.md`

状态只能是：

- `CONFIRMED_EXACT_UNIT`
- `CONFIRMED_MODEL_ONLY`
- `PROBABLE_MODEL`
- `UNKNOWN`

没有序列号/设备绑定证据时，不得写 exact unit。

---

## 6. 建立 G2 参数清单

建立：

`G2_CALIBRATION_INPUT_MATRIX.csv`

至少包含：

| 参数类别 | 参数 | 当前值 | 单位 | 状态 | 来源 | 是否需实测 | 备注 |
| --- | --- | --- | --- | --- | --- | --- | --- |

参数至少覆盖：

### 光谱/辐射
- spectral band
- spectral response / RSR
- radiometric output definition
- temperature conversion availability
- emissivity setting
- reflected apparent temperature setting
- atmospheric compensation inputs

### 光学
- lens/focal length
- F-number（若适用/可得）
- FOV
- focus state
- optical transmission
- PSF / MTF / edge response

### 探测器/采样
- detector resolution
- pixel pitch
- frame rate
- integration/exposure time
- bit depth
- ADC behavior
- gain mode

### 噪声/校正
- NETD（官方值单列，不等于本机实测）
- temporal noise
- fixed-pattern noise
- NUC behavior
- bad-pixel correction
- AGC/display mapping
- temporal filtering

### 几何/时序
- RGB/IR extrinsics（若为双传感器）
- timestamp behavior
- synchronization
- rolling/global integration behavior（若相关）

---

## 7. 官方资料与实测值严格分开

所有值必须带证据类型：

- `MANUFACTURER_SPEC`
- `FILE_METADATA`
- `PROJECT_RECORD`
- `MEASURED_THIS_UNIT`
- `ASSUMED`
- `UNKNOWN`

例如厂商写：

`NETD < 40 mK`

只能记录为 manufacturer spec。

除非对当前具体设备完成可追溯测量，否则：

`measured_NETD = UNKNOWN`

---

## 8. 建立最小 G2 实测计划

如果参数无法从现有证据获得，设计最小可执行标定计划。

输出：

`G2_MINIMUM_MEASUREMENT_PLAN.md`

至少分：

### G2-A 均匀场/黑体
用于：
- 响应一致性；
- offset/gain；
- temporal noise；
- fixed-pattern behavior；
- NUC 前后行为；
- DN 与温度/辐亮度关系（若设备支持）。

### G2-B 空间响应
采用合适的边缘/点/狭缝目标，用于估计：
- PSF/MTF 或等价空间响应；
- 亚像素/像元积分相关行为。

### G2-C 时间响应
用于：
- 帧间响应；
- temporal filtering；
- 积分/曝光相关行为；
- 热启动与稳定时间（若会影响数据）。

### G2-D 环境记录
每次标定至少记录：
- 环境温度；
- 湿度；
- 目标距离；
- 黑体/目标温度；
- 相机设置；
- NUC/AGC；
- lens/focus；
- 采集时间；
- 原始文件 SHA。

不要假定实验室已有黑体；若没有，列为设备需求，不伪造替代测量等价性。

---

## 9. G4 独立真实留出合同

建立：

`G4_HOLDOUT_CONTRACT.md`

必须定义什么数据才有资格作为 G4：

- 独立采集组；
- 不用于任何仿真调参；
- 不用于相机参数拟合；
- 不用于热模型参数拟合；
- 不用于阈值选择；
- 不用于失败样本人工修正规则制定；
- 不用于下游模型训练/选择（若评估该泛化目标）。

每个候选真实源标记：

- `ELIGIBLE_HOLDOUT`
- `CALIBRATION_ONLY`
- `DEVELOPMENT_ONLY`
- `INELIGIBLE_CONTAMINATED`
- `UNKNOWN_PROVENANCE`

并说明原因。

---

## 10. 数据授权与隐私/发布边界

对每个真实源记录：

- provider
- ownership
- research-use permission
- redistribution permission
- publication permission
- derivative/synthetic comparison permission

没有证据时写 `UNKNOWN`。

不能把“本地能打开”当作“可以公开发布”。

---

## 11. 不修改既有主链

保护：

`D:\AgentOS\Projects\2026-09-26-多尺度热红外仿真数据研究`

本轮禁止修改：

- G1/R4 历史输出；
- R4 manifest；
- P1 配对样本；
- IR 数值模块；
- Avata 2 production asset；
- 比赛分类器。

允许新增审计报告、CSV、JSON 和任务状态记录。

---

## 12. 验收结果

本任务完成后必须能回答：

1. 真实热像设备型号是否已确认？
2. 是否确认到具体设备实例？
3. 镜头/FOV/波段/分辨率/像元等哪些是官方值？
4. 曝光/积分时间是否可知？
5. NUC/AGC 是否可知？
6. 原始数据是否辐射型/测温型/显示型？
7. 哪些参数只能通过实测获得？
8. 现有真实数据有几个独立采集组？
9. 哪些能作为 calibration？
10. 哪些有资格作为 G4 holdout？
11. 授权状态如何？
12. 下一步是否具备启动实际 G2 测量的条件？

---

## 13. 允许的最终状态

G2：

- `INPUT_CONTRACT_READY`
- `PARTIAL_INPUTS`
- `BLOCKED_MISSING_DEVICE_INFO`
- `BLOCKED_MISSING_CALIBRATION_EQUIPMENT`

G4：

- `HOLDOUT_CONTRACT_READY`
- `HOLDOUT_IDENTIFIED_NOT_FROZEN`
- `BLOCKED_NO_INDEPENDENT_SOURCE`
- `BLOCKED_UNKNOWN_PROVENANCE`

本轮不得宣布：

- `G2 PASS`
- `G4 PASS`
- `REALISTIC IR VALIDATED`

除非任务范围被用户重新授权并且实际完成相应独立验证。

---

## 14. 交付

至少生成：

- `P2-001_CHINESE_REVIEW.md`
- `REAL_CAMERA_IDENTITY_AUDIT.md`
- `REAL_SOURCE_MANIFEST.csv`
- `G2_CALIBRATION_INPUT_MATRIX.csv`
- `G2_MINIMUM_MEASUREMENT_PLAN.md`
- `G4_HOLDOUT_CONTRACT.md`
- `LICENSE_AND_PROVENANCE_AUDIT.md`

完成后停止。

不要启动 M5。
不要自动开始实际黑体采集。
不要修改主 IR 链。
