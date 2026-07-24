# 流哨 Stream Sentinel｜直播流检测与流媒体巡检取证工具

> 把 HLS、RTSP、UDP/RTP、RTMP、SRT 等直播流“能不能播、哪里异常、证据是什么”变成一份可交付的巡检报告。

Stream Sentinel 是面向酒店 IPTV、安防视频、教育录播、园区组播和直播运维的本地 Windows 工具。无需部署服务器、无需配置环境，双击即可批量检测直播流地址，采集媒体参数、首帧截图、组播网卡尝试轨迹，并导出 HTML 巡检取证报告。

如果这个工具帮你节省了现场排障时间，欢迎在 GitHub 点 Star、在 Gitee 点 Star/点赞。早期项目很需要这些反馈，它会直接影响后续功能优先级和专业版支持力度。

## 下载体验版

- [GitHub Releases 下载 Windows 体验版](https://github.com/ITIAN-CAO/stream-sentinel/releases/latest)
- [Gitee Releases 下载 Windows 体验版](https://gitee.com/ITIAN_chaoqian/stream-sentinel-mirror/releases/tag/v2.2.6-trial)

体验版无需注册、无需联网激活、没有使用期限，保留协议探测、媒体参数、UDP 网卡识别、首帧截图和 HTML 报告能力；最多保存 3 条流，仅支持手动巡检，报告带体验版标识。专业版提供不限流、定时巡检与正式交付报告。

![Stream Sentinel 直播流检测工作台](docs/product-screenshot.png)

## 产品截图与演示素材

这张工作台截图可以直接用于 GitHub、Gitee、掘金、微信群、朋友圈和私聊试用介绍：

![流哨 Stream Sentinel 直播流检测、RTSP/HLS/UDP 流媒体巡检工作台](docs/product-screenshot.png)

推广时建议把截图放在正文第一屏，让用户先看到“批量流地址、协议、状态、响应、媒体参数、诊断结果”这些真实界面信息，再看功能说明。仓库内还准备了 [推广素材包](docs/promotion-kit.md)，包含平台标题、首发正文、私聊话术、60 秒演示视频脚本、定价策略和首批客户验证表。

## 适合谁

- 酒店 IPTV、园区电视、校园电视的组播验收与日常巡检；
- 安防集成商、NVR/摄像机项目、教育录播平台的批量流检测；
- 直播技术、运维工程师在切源、上线、故障沟通前做可用性确认；
- 需要把“播放异常”说清楚、留证据、交付给客户或供应商的人。

## 核心卖点

### 不只是端口探测，而是直播流播放证据

- 检测可用性、响应耗时、HTTP 状态、协议类型和诊断结论；
- 自动提取分辨率、帧率、视频/音频编码、码率、采样率和声道；
- 支持一键截取首帧，作为现场验收、供应商沟通和故障复盘证据；
- 导出独立 HTML 报告，不依赖平台账号或外部服务。

### HLS、RTSP、UDP 组播场景更专业

- HLS 展示片段数量、变体、目标时长、最新片段、结束标记、间断次数和加密状态；
- RTSP/RTMP/SRT 借助随包集成的 `ffprobe.exe` 采集真实媒体流参数；
- UDP/RTP 自动遍历本机活动网卡，记录包数、字节数、包速率和尝试轨迹；
- 成功接收的网卡会被学习并保存，下一轮巡检优先复用。

### 面向现场的易用设计

- 从 Excel 直接粘贴两列：`名称 + Tab + 流地址`，也支持只粘贴地址；
- 自动提示格式异常行，自动跳过重复地址；
- 可设置探测超时、并发数、接收网卡、巡检频率和自定义分钟数；
- 内置酒店 IPTV 验收、安防视频巡检、直播源巡检三套模板；
- 流资产、最佳网卡、巡检计划、历史记录和首帧证据全部本地持久化。

## 支持协议

| 类型 | 支持情况 | 典型用途 |
| --- | --- | --- |
| HLS / HTTP / HTTPS | 支持 | 直播清单、点播、网页媒体资源 |
| RTSP | 支持 | 摄像机、NVR、安防平台 |
| UDP 组播 / RTP | 支持 | 酒店 IPTV、园区电视、广播组播 |
| RTMP / SRT | 支持 | 直播推拉流、远程传输 |

UDP 组播地址示例：`udp://@239.1.1.1:1234`

## 3 分钟快速开始

1. 解压发行包；体验版双击 `stream-sentinel-v2.2.6-trial.exe`。
2. 浏览器会自动打开本地工作台；程序找不到默认端口时会自动选择可用端口。
3. 在“添加地址”单条录入，或直接从 Excel 粘贴：

   ```text
   酒店大厅直播    http://example.com/live/index.m3u8
   前台摄像机      rtsp://example.com/live
   ```

4. 按场景选择模板，例如酒店 IPTV 验收、安防视频巡检或直播源巡检。
5. 点击“开始巡检”。对 UDP/RTP 流保持“接收网卡：自动选择”，工具会自行尝试活动网卡。
6. 点击流名称查看完整技术详情；需要取证时点击“截取首帧”。
7. 点击“导出巡检报告”，得到可独立转发的 HTML 文件。

## 你会看到哪些信息

- 地址、协议、检测时间、响应耗时和诊断结论；
- 媒体指纹：编码、分辨率、帧率、音频、码率；
- HLS 清单证据：片段、变体、加密与间断；
- UDP/RTP 网络证据：选中的网卡、收包统计与网卡尝试轨迹；
- 故障建议：网络超时、鉴权失败、组播无包等对应的排查方向。

## 本地数据与隐私

所有流地址、巡检记录和截图都保留在你的电脑上，不上传到云端。运行后，程序目录会自动创建：

- `data/streams.json`：流资产与已学习的最佳网卡；
- `data/schedules.json`：定时巡检、并发和模板配置；
- `data/history.jsonl`：巡检历史；
- `captures/`：首帧证据文件。

这些内容不会写入发行 ZIP。你可以直接复制整个程序目录做本地备份或迁移。

## 运行环境

- Windows 10 / Windows 11 64 位；
- 建议使用新版 Chrome 或 Edge；
- 包内已包含 `ffprobe.exe` 与 `ffmpeg.exe`，无需另行安装或配置 PATH；
- 无需数据库、服务器、账号或联网激活。

> 当前版本不支持 Windows 7 / 8 / 8.1 或 32 位 Windows。具体流的可探测性仍取决于你是否拥有访问权限，以及现场网络、VLAN、IGMP、鉴权和防火墙配置。

## 升级专业版

专业版提供不限流地址、定时巡检、无体验版标识报告和项目场景支持。首发阶段建议价为 **199 元/台买断**；协议适配、报告字段、现场网络或项目部署需求单独报价。

可在 [GitHub Issues](https://github.com/ITIAN-CAO/stream-sentinel/issues) 或 [Gitee Issues](https://gitee.com/ITIAN_chaoqian/stream-sentinel-mirror/issues) 留言“专业版试用/购买”。请勿在公开 Issue 中提交真实流地址、账号、Token 或客户网络信息。

## 支持项目

如果你觉得 Stream Sentinel 对直播流检测、RTSP/HLS 排障、UDP 组播验收有帮助：

- 在 GitHub 点一个 Star：[ITIAN-CAO/stream-sentinel](https://github.com/ITIAN-CAO/stream-sentinel)
- 在 Gitee 点 Star/点赞：[ITIAN_chaoqian/stream-sentinel-mirror](https://gitee.com/ITIAN_chaoqian/stream-sentinel-mirror)
- 把体验版转给做 IPTV、安防、教育录播、直播运维的朋友试用

真实 Star、Issue 和试用反馈会优先转化为后续功能，例如更丰富的报告模板、批量项目空间、异常趋势分析和更多协议细节展示。

## 使用边界与许可证

请仅检测你拥有授权的流地址。包内第三方组件的许可证见 [LICENSES](LICENSES/) 目录。
