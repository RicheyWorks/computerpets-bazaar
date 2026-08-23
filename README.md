# Bazaar

**NFT Marketplace** — Web portal for trading pets, traits, and in-game items under the ComputerPets canon.

Part of the [ComputerPets](https://github.com/RicheyWorks/computerpets) ecosystem. Index: [computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem).

> Status: **design scaffold**. This repository ships the contract, README, and layout so implementation can start without renaming the organ later.

## Why it exists

Flagship already verifies Ethereum NFT ownership. Bazaar is the storefront: listings, royalties, and trait swaps — never a random OpenSea skin dump.

The flagship overlay already puts a living sticker on the real desktop (Rui first, 210 kinds). Bazaar does not replace that. It is one organ.

## Stack

TypeScript · React 19 · Vite · wagmi / viem · Spring + web3j listings API · IPFS metadata

GroupId / namespace: `com.enterprisepet.bazaar`  
Default listen: `8080`

## Talks to

- computerpets-minter
- computerpets-ledger
- computerpets-atelier
- computerpets Spring NFT verifier

## Contract

### Data

`Listing(id, tokenId, priceWei, seller) · Fill(txHash, buyer) · RoyaltySplit(bps, address)`

### Surface

- GET /v1/listings?species=&slot= — active asks
- POST /v1/listings — signed ask from a verified owner
- POST /v1/fill — escrow + transfer via Minter
- GET /v1/royalties/{collection} — creator cuts

### Failure doctrine

Chain reorg → listing frozen until confirmations. Unverified Steam-only pet → cannot list on-chain. Wallet reject → no partial debit.

## Layout

```
computerpets-bazaar/
  README.md           this file
  LICENSE             MIT
  docs/CONTRACT.md    the same contract, frozen for implementers
  src/                implementation lands here
```

## Run (Windows)

PowerShell, from this folder, after the flagship helpers (Git, Node LTS 22+, JDK 21 as needed):

```powershell
cd app; npm install; npm run dev
```

You do not need this service to meet Rui. The [flagship start-here](https://github.com/RicheyWorks/computerpets/blob/main/docs/START-HERE.md) is still the first pet.

## Ecosystem

| Organ | Repo |
| --- | --- |
| Flagship desktop + Spring | [RicheyWorks/computerpets](https://github.com/RicheyWorks/computerpets) |
| This organ | [RicheyWorks/computerpets-bazaar](https://github.com/RicheyWorks/computerpets-bazaar) |
| Full map | [RicheyWorks/computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem) |

## License

MIT. See [LICENSE](LICENSE).

---

*Two hundred ten living kinds. Keep them so a line does not go quiet.*
