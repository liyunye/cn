## 专业术语

| 术语       | 定义                                                      |
|:----:|:----:|
| BGW            | Border Gateway，边界网关，外部访问VPC内业务的流量终结点          |
| VPN Connection | 云端和客户端VPN网关之间多个VPN Tunnel的逻辑集合，对VPN Tunnel进行统一管理 |
| VPN Tunnel     | 云端和客户端VPN网关之间的IPsec隧道，对于客户流量进行加密传输                                        |
| BGP            | Border Gateway Protocal，边界网关协议，用于云端和客户端VPN网关之间路由数据，推荐使用BGP协议进行路由                            |
| VPNHub               |   连接到同一个边界网关的多个客户端的VPN隧道之间支持进行流量转发，而无需在多个客户端之间再次建立新的VPN连接                                                               |
