# 停止运营与归档声明 · Shutdown & Archive Notice

**停止时点 / Shutdown point：2026-11-23 09:36（UTC+8，Asia/Shanghai）= 2026-11-23T01:36Z**

本项目已于上述时点停止运营并归档。该时点是唯一有效的“停止时点”，此后一切关于本项目的追问都以该时点及本文档所列证据为准。

This project ceased operation and was archived at the time above. That single timestamp is the authoritative shutdown point for any later inquiry.

---

## 当前状态 / Current status

| 项目 / Item | 状态 / Status |
| --- | --- |
| 对外可调用端点 / Public endpoints | 无 / None — 所有托管实例已删除，匿名请求不再返回任何业务数据 |
| 前端托管 / Frontend hosting | 已删除 / Deleted — `cqnb52nacm5j`（tianacloud.site）实例已删除，域名仅剩平台登录跳转 |
| 后端服务 / Backend service | 已删除 / Deleted — `fn-t63QxJ01A7OFP3WXHpxxFHyw` 实例与构建产物已删除 |
| API 密钥、Webhook 签名密钥 / API & webhook keys | 全部吊销 / All revoked — 数据库访问令牌（secret）已移除并复核为空 |
| 商户接入 / Merchant onboarding | 无 / None — 未接入任何商户，未产生任何实际收单、结算、兑换或代付 |
| 资金流转 / Fund movement | 无 / None — 停止后不再发生任何资金流转 |
| 新版本部署 / New deployments | 不再进行 / None |

## 关于链上合约 / On-chain contracts

已部署的合约无法从链上删除，只能声明弃用：

> **原合约地址及仓库中出现的任何关联地址均已弃用。请勿向该地址或任何关联地址转账、授权或交互。**
> All previously deployed contract addresses, and any associated addresses appearing in this repository, are deprecated. Do not send funds to, approve, or interact with them.

## 代码用途 / Permitted use of the code

历史代码仅作技术存档，**不得用于实际收单、结算、兑换或代付**。
作者不提供任何形式的接入支持、部署协助或技术咨询。

Archived code is for technical reference only and must not be used for live payment collection, settlement, exchange, or payout. The author provides no integration support, deployment assistance, or technical consulting of any kind.

## 已移除的接入与部署内容 / Removed integration & deployment material

- `demo/`：对外演示前端（已移除，不再提供线上演示）
- `examples/testnet/`：接入闭环脚本样例（已移除）
- `sdk/README.md`：接入指引改写为“已停止，不再提供接入”
- 生产网关、签名密钥、地址池、商户数据从未公开，也不在任何存档中

## 证据 / Evidence

停止流程的机器证据（探测结果、吊销记录、删除回执、时间戳）随归档包一并留存，包含：

1. 端点探测前后对比：停用前 web 端返回 303 登录跳转、函数端点返回 `401 FETCH_AUTH_REQUIRED`；停用后两者均为无业务数据的平台层响应（303 / 401），不再有任何可执行的服务端逻辑
2. 密钥吊销记录：`secrets remove` 回执 + 吊销后再查询为空
3. 托管与函数删除回执：`web delete`（`state=deleted`）、`function delete`（实例列表 total=0）
4. 本仓库归档标记（archived、只读）与 `shutdown-20261123` 标签及最后提交哈希

## 通知 / Notification

已接触方（如有）已按下列口径书面告知：本项目停止服务，即日起不再提供任何收款、结算或技术支持；请立即停止使用相关接口与地址并自行迁移至合规渠道；此前任何约定一并终止；已发生的资金请自行清算，作者不参与后续处理。

---

*本声明中英文版本内容一致；如有歧义，以中文版本为准。*
