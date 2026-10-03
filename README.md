# VPN Gate + Cloudflare EdgeTunnel 链式代理与家宽住宅节点监控系统

本项目基于 **VPN Gate 原生住宅节点** 与 **Cloudflare EdgeTunnel 边缘中继代理**，实现无需 VPS、纯正原生家宽落地、永久免费不限流量的代理网络。

## 核心部署架构

- **检测端 Worker**: [gate-check.988228.xyz](https://gate-check.988228.xyz/ip.json) (部署在 Cloudflare 边缘节点，并发检测 SSTP/SOCKS5 连通性并识别出口 ISP 住宅属性)
- **EdgeTunnel 前置节点**: [gate-edge.988228.xyz](https://gate-edge.988228.xyz) (VLESS over WebSocket，前置加速 + 链式转发)
- **GitHub Actions 测速构建**: 每 30 分钟定时自动从 VPN Gate 抓取最新节点，并发调用检测 Worker 测速、过滤死节点并分类
- **GitHub Pages 展示与订阅源**:
  - 前端监控大盘: [https://donxan.github.io/vpngate-edgetunnel/](https://donxan.github.io/vpngate-edgetunnel/)
  - EdgeTunnel 自定义节点池: [https://donxan.github.io/vpngate-edgetunnel/nodes.txt](https://donxan.github.io/vpngate-edgetunnel/nodes.txt)
