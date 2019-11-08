## 基础架构

#### 概述

VPN整体架构图如下：

 ![](/image/Networking/Direct-Connect-Service/Infrastructure.png)

#### VPN的组件

VPN
- 客户网关(Customer Gateway)：Site-To-Site VPN客户侧设备在云端的逻辑组件。
- VPN连接(VPN Connection)：在边界网关和客户网关之间建立的一组Site-To-Site IPsec VPN隧道的集合，对这些IPsec隧道进行统一管理，包括统一设置路由方式、连接类型等。
- VPN隧道(VPN Tunnel)：在边界网关和客户网关之间建立的一组Site-To-Site IPsec VPN隧道，用于承载业务流量并对数据执行加解密。

边界网关
- 边界网关(BGW，Border Gateway)：京东云基于边界网关和客户网关建立Site-To-Site VPN，边界网关在此过程中作为京东云端VPN设备的逻辑组件，为客户提供IPsec VPN服务。

#### 高可用架构

VPN的云端网关和隧道均采用高可用架构设计，其中：
- 创建VPN连接时，会自动分配两个云端的公网IP，作为云端的VPN网关IP，用于和客户网关间建立Site-To-Site VPN。
- 推荐客户端使用两台VPN设备，各配置一个公网IP，与京东云建立VPN连接。
- 建议在每个云端的公网IP和每个客户端的公网IP之间分别建立VPN隧道，同时使用BGP路由协议，以保证流经VPN隧道的客户业务数据不间断通信。
