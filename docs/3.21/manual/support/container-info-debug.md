# 容器信息排错指南

## 服务详情列表
`运行中` 列表代表当前运行容器的列表, 包括已健康或未健康容器

`已停止` 列表代表该服务历史容器列表, 容器停止可能有以下几种情况:
- 服务更新(重启)部署滚动更新产生的历史容器
容器状态 Error, exit-code为 137, 143 等
- 服务自身退出产生的历史容器
容器状态 Error, exit-code为容器主进程退出码
- 服务健康检查未通过被kill产生的历史容器
容器状态 Error, exit-code为 137, 143 等
- 状态为`Set Dead by gc`, 这个状态是 dice 同步底层容器状态未收集到该容器信息而设置的, 与业务状态无关



## pod详情列表

pod详情列表代表当前运行的该服务的 pod, 与服务详情列表中的容器列表有对应关系

pod详情列表中的 `停止` 操作表示停止该pod, 停止后会有新的pod被拉起


