# Agent ID Check-in Board

A public check-in board exclusively for **Binance Agent ID** holders, built for the
**Agent ID Hackathon** (Binance Wallet × BNB Chain, submissions close 9 Dec 2026).

**Live board:** https://xcaracalid.github.io/agent-id-checkin-board/

## How it works

- The board's only key is a Binance Agent ID. The smart contract's single core
  function, `checkIn(string)`, calls `balanceOf(msg.sender)` on the SPACE ID
  Agent ID contract and reverts for any address that does not hold one.
- Each check-in stores a short public message (max 280 chars) on-chain with the
  sender and timestamp — every interaction is, by construction, an interaction
  by a verified Agent ID holder.
- This page connects a wallet on BNB Chain, verifies Agent ID ownership,
  submits the check-in, and renders the live board from the contract's
  read-only views (`totalCheckIns`, `latestCheckIns`, `checkInCount`).

## Safety posture

- The contract moves **no assets**: zero payable functions, no transfers, no approvals.
- **No owner or admin role** exists — no mint, pause, freeze, or withdraw power.
- Agent ID is used only as an ownership gate, never to look up other people's wallets.
- No rewards or returns are promised for checking in.

## Contract

- **AgentIDCheckinBoard** (BNB Chain mainnet):
  [`0x7ec77bAa144eb36554d50d425A57330cbF38B687`](https://bscscan.com/address/0x7ec77bAa144eb36554d50d425A57330cbF38B687)
- Source verified on Sourcify — exact match (creation + runtime).
- Agent ID gate: SPACE ID Agent ID, `0x60B9262456dE011F7d15a54CdD8c48bAaa8B022F`.

## Files

- `index.html` — the whole app (single page, no build step).
- `ethers.umd.min.js` — ethers v6.13.4, vendored locally so the page has no CDN dependency.
