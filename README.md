> **本项目已于 2026-11-23 停止运营并归档。**
> 当前状态：无部署、无对外可调用端点、无商户接入、无任何资金流转。
> 历史代码仅作技术存档，不得用于实际收单、结算、兑换或代付。
> 作者不提供任何形式的接入支持、部署协助或技术咨询。
> 原合约地址已弃用，请勿向该地址或任何关联地址转账。
>
> **This project was shut down and archived on 2026-11-23.** No deployments, no public endpoints, no merchant onboarding, no fund flow. Historical code is for technical reference only and must not be used for live collection, settlement, exchange, or payout. All previously deployed contract addresses are deprecated — do not send funds to them. Details: [SHUTDOWN.md](SHUTDOWN.md)

# Aegis Chain

> Non-custodial multi-chain payment & donation gateway — invoices, on-chain settlement, cross-chain intents, mobile checkout. Core production engine is closed; the demo, SDK, mobile shell and docs are open under MIT.
>
> 非托管多链收款与捐赠网关：收款单、链上结算、跨链意图、手机收银台。**核心生产引擎闭源，演示前端 / SDK / 安卓壳 / 文档以 MIT 开源。**

[中文文档](docs/i18n/README.zh.md) · [English](docs/i18n/README.en.md) · [Français](docs/i18n/README.fr.md) · [한국어](docs/i18n/README.ko.md) · [日本語](docs/i18n/README.ja.md) · [Русский](docs/i18n/README.ru.md) · [Bahasa Indonesia](docs/i18n/README.id.md) · [Español](docs/i18n/README.es.md) · [العربية](docs/i18n/README.ar.md)

---

## Try it in 10 seconds

Open [`demo/index.html`](demo/index.html) in a browser — double-click, no build, no server, no wallet. It runs a full invoice → deposit → confirmation flow against an in-memory mock. Nothing on screen touches real funds.

Then install the Android shell from the [latest release](https://github.com/ugjdygh/aegis-chain/releases/latest) and point it at your own gateway.

## What is open, what is closed

| Open — MIT | Closed — proprietary |
| --- | --- |
| [`demo/`](demo/) mobile demo: invoice flow, mock chain, zh/en today — more languages wanted | Production gateway (`src/`), chain scanners, RPC failover, reconciliation |
| [`sdk/`](sdk/) merchant client: create invoice, poll, verify HMAC webhook | `PaymentHub` settlement contract source and deployment scripts |
| [`mobile-shell/`](mobile-shell/) Android WebView shell, three build variants | Address pools, signing keys, production endpoints, merchant data |
| [`examples/`](examples/) Base Sepolia walkthrough, sample payloads | Sanctions screening lists and operational runbooks |
| [`docs/`](docs/) architecture, features, compliance, nine languages | |

The boundary is deliberate and written down in [`docs/OPEN-SCOPE.md`](docs/OPEN-SCOPE.md). If a feature you need is closed, open an issue describing what you must verify or integrate — do not ask for the engine.

## Good first issues — start here

No blockchain experience needed for most of them.

| Label | What it means | Typical task |
| --- | --- | --- |
| `good first issue` | Self-contained, one file, clear acceptance | Fix a typo, add a wallet deep-link example, tighten mobile layout |
| `i18n` | Translation of `demo/` and docs | Complete Korean / Japanese / Russian / Indonesian UI strings |
| `docs` | Documentation correctness | A step in the Termux guide that does not work on your phone |
| `android` | `mobile-shell/` | Reproduce a WebView issue, improve offline page copy |
| `testnet` | Base Sepolia walkthrough | Run the example flow end-to-end and report what broke |
| `help wanted` | Bigger, still scoped | SDK examples for Python / PHP, accessibility pass |

Every issue states scope, acceptance criteria and which directory it touches. If an issue is unclear, say so in the thread — that is a docs bug too.

## How contribution works

1. Pick an issue tagged `good first issue`, `i18n`, `docs`, `android` or `testnet`.
2. Comment "I'll take this" so nobody duplicates work.
3. Branch, make the change, run what the PR template asks for.
4. Open a PR. Review checks cover translation completeness, demo smoke test and shell build.
5. Merge, and you are credited in the release notes.

Contribution scope, style rules and the "never submit this" list are in [CONTRIBUTING.md](CONTRIBUTING.md).

## Layout

```
demo/            self-contained mobile demo (mock chain, zh/en today)
sdk/             merchant client + webhook signature verification
mobile-shell/    Android WebView shell (dev / test / prod variants)
examples/        Base Sepolia walkthrough and sample payloads
docs/            architecture, features, compliance, security, i18n (9 languages)
.github/         issue forms, PR template
```

## Three builds, one feature set

Dev, test and production Android builds load the same server code and differ only in gateway URL, package name and app label. A parity gate compares APK entry sets, shared asset hashes and the three gateways' `/api/features` manifests; any divergence fails the check instead of shipping.

## Documentation

[Architecture](docs/ARCHITECTURE.md) · [Features](docs/FEATURES.md) · [Support / donations](docs/SUPPORT.md) · [Compliance](docs/COMPLIANCE.md) · [Roadmap](docs/ROADMAP.md) · [Changelog](CHANGELOG.md) · [Open scope](docs/OPEN-SCOPE.md) · [Security](SECURITY.md) · [Contributing](CONTRIBUTING.md)

## License

- `demo/`, `sdk/`, `mobile-shell/`, `examples/` — MIT, see [LICENSE](LICENSE)
- `docs/` — CC BY 4.0
- Core production implementation — **not licensed, not distributed**; see [`LICENSES.md`](LICENSES.md)

## Status

Version 0.5.0 — Base mainnet and Base Sepolia verified against live chains; unit tests and end-to-end checks passing; dev / test / prod builds verified feature-identical. Not audited, not production-hardened. Do not route real customer funds through it.

## Compliance boundary

Non-custodial software only: no custody, no fiat on/off-ramp, no token issuance, no self-built bridge. Under EU MiCA this is software provision, not a CASP service; adding custody, exchange or fiat conversion would require a licence an individual cannot obtain. See [COMPLIANCE.md](docs/COMPLIANCE.md).
