# Bazaar

**A species-aware storefront for pets, traits, and items.**

A planned marketplace that verifies ownership and routes trades through the ComputerPets minting and ledger services.

**Stage: design scaffold.** This checkout contains a design document and a source placeholder. The experience below is planned; there is no runnable app or integrated service yet.

[Status](#status) · [Planned experience](#planned-experience) · [Contributor quickstart](#contributor-quickstart) · [Service contract](docs/CONTRACT.md) · [Ecosystem map](https://github.com/RicheyWorks/computerpets-ecosystem)

## Status

| Available today | What you can inspect |
| --- | --- |
| [Service contract](docs/CONTRACT.md) | Intended behavior, boundaries, and planned dependencies. |
| [Source placeholder](src/bazaar/index.ts) | Name metadata only; no package.json, app, or runtime is checked in. |
| [MIT license](LICENSE) | Licensing terms for the repository. |

Gameplay, endpoints, integration arrows, and failure handling on this page describe implementation targets. No build/test harness, CI workflow, or product screenshots are included in this scaffold.

## Planned experience

- GET /v1/listings?species=&slot= — active asks
- POST /v1/listings — signed ask from a verified owner
- POST /v1/fill — escrow + transfer via Minter
- GET /v1/royalties/{collection} — creator cuts

### Planned technology

TypeScript · React 19 · Vite · wagmi / viem · Spring + web3j listings API · IPFS metadata

### Planned connections

These arrows show intended dependencies, rather than working integrations.

```mermaid
flowchart LR
  owner -->|ask| bazaar
  bazaar --> minter
  bazaar --> ledger
  atelier -->|thumb| bazaar
```

## Contributor quickstart

With access to this private repository, Git and PowerShell are enough to review the scaffold:

```powershell
git clone https://github.com/RicheyWorks/computerpets-bazaar.git
Set-Location computerpets-bazaar
Get-Content docs/CONTRACT.md
Get-Content src/bazaar/index.ts
```

Read [Service contract](docs/CONTRACT.md) before choosing implementation details. The commands above inspect the checked-in files; app installation, editor launch, and server startup become possible after a buildable project and entry point are added.

### First implementation target

**Read-only listing grid filtered by species + one signed ask flow against a test NFT.**

You know it works when: Unverified pet cannot list. Wallet reject: no ledger debit. Reorg: listing frozen until confirms.

Treat this as an acceptance target for a future implementation. Start with the documented slice, add the required project setup and focused tests, and update these instructions with commands that work from a fresh clone.

## Design boundaries

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

**Required failure behavior:**

Chain reorg → listing frozen until confirmations. Unverified Steam-only pet → cannot list on-chain. Wallet reject → no partial debit.

## Ecosystem

- [computerpets-minter](https://github.com/RicheyWorks/computerpets-minter)
- [computerpets-ledger](https://github.com/RicheyWorks/computerpets-ledger)
- [computerpets-atelier](https://github.com/RicheyWorks/computerpets-atelier)
- [computerpets](https://github.com/RicheyWorks/computerpets) Spring NFT verifier

Start with the [ComputerPets flagship](https://github.com/RicheyWorks/computerpets) for the desktop pet. This repository describes an optional extension; the [ecosystem map](https://github.com/RicheyWorks/computerpets-ecosystem) explains the broader plan.

## License

MIT. See [LICENSE](LICENSE).
