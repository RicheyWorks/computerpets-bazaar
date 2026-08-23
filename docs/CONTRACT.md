# Bazaar contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Bazaar**
- Repo: `computerpets-bazaar`
- Category: Web & Client
- Idea: NFT Marketplace
- Port / surface: `8080`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Listing(id, tokenId, priceWei, seller) · Fill(txHash, buyer) · RoyaltySplit(bps, address)

## Surface

- GET /v1/listings?species=&slot= — active asks
- POST /v1/listings — signed ask from a verified owner
- POST /v1/fill — escrow + transfer via Minter
- GET /v1/royalties/{collection} — creator cuts

## Neighbors

- computerpets-minter
- computerpets-ledger
- computerpets-atelier
- computerpets Spring NFT verifier

## Failure doctrine

Chain reorg → listing frozen until confirmations. Unverified Steam-only pet → cannot list on-chain. Wallet reject → no partial debit.

## Stack

TypeScript · React 19 · Vite · wagmi / viem · Spring + web3j listings API · IPFS metadata
