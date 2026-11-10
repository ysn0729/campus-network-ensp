# 设备配置说明

本目录下每份文件都是从 eNSP 工程里导出的设备启动配置（VRP 纯文本，未删改）。
导入方式：登录设备 → `system-view` → 整体粘贴 → `save` → 按 `y`。

| 文件 | 设备 | 型号 | 关键配置 |
|---|---|---|---|
| `ISP.cfg` | ISP | AR1220 | 两个上行口 202.101.1.0/30、202.102.1.0/30，模拟运营商 |
| `FW1.cfg` | FW1 | USG6000V | HRP 主动、NAT 地址池、安全策略、OSPF |
| `FW2.cfg` | FW2 | USG6000V | HRP 备机、跟随同步 |
| `Core-SW1.cfg` | Core-SW1 | S5700 | 7 个 VLANIF、VRRP、MSTP instance 1 根、OSPF+BFD、DHCP 池 ×4 |
| `Core-SW2.cfg` | Core-SW2 | S5700 | 同上，MSTP instance 2 根，DHCP 池 vlan30/vlan40 |
| `Agg-SW1.cfg` | Agg-SW1 | S5700 | 双上联核心、VLAN 透传、管理地址 .11 |
| `Agg-SW2.cfg` | Agg-SW2 | S5700 | 同上，.12 |
| `Agg-SW3.cfg` | Agg-SW3 | S5700 | 同上，.13 |
| `Access-1A.cfg` | Access-1A | S5700 | 上联 trunk、AP/PC 接入口、DHCP Snooping |
| `Access-1B.cfg` | Access-1B | S5700 | 病区接入 |
| `Access-2A.cfg` | Access-2A | S5700 | 门诊接入 + AP-2 |
| `Access-2B.cfg` | Access-2B | S5700 | 办公接入 |
| `Access-3A.cfg` | Access-3A | S5700 | 办公接入 + AP-3 |
| `Access-3B.cfg` | Access-3B | S5700 | 访客接入 |
| `Server-SW.cfg` | Server-SW | S5700 | 服务器区接入，VLAN200 |
| `AC-1.cfg` | AC-1 | AC6005 | CAPWAP 源、SSID/VAP/AP 组、AP MAC 认证 |

## 关于口令

配置中的口令、密钥均为实验值（例如无线口令 `Hospital@123`），不对应任何真实系统，可放心公开。

## 关于缺失项

- 部分终端（PC、Client、STA）没有配置文件，它们是 eNSP 的图形化仿真终端，靠界面填 IP/SSID；
- `configs/` 只覆盖 16 台可配置的网络设备。