# Simplicity Confidential Vault (prototype)

This repository contains a **prototype** Simplicity/SimplicityHL confidential smart contract for Bitcoin/Elements/Liquid environments:
- A SimplicityHL source implementing a **confidential vault**: multisig + timelock + emergency recovery.
- A combinator-tree text representation (informational).
- Build/run scaffolding and notes.

**Important:** This is a research/prototype artifact. I have *not* executed or formally verified these files here.
You will need the official Simplicity toolchain (Blockstream / Elements Simplicity compiler/interpreter) to compile, typecheck, and verify. See `tools/README.md` for links and setup notes.

## Contents
- `contracts/vault.simphl` — SimplicityHL (human-friendly) source for the vault contract.
- `contracts/vault_tree.txt` — combinator-style outline of the compiled logic.
- `examples/usage.md` — how the contract would be used with peg-in/out and PSETs (Partially Signed Elements Transactions) and Confidential Transactions.
- `tools/build.sh` — placeholder build script showing typical steps (requires local Simplicity toolchain).
- `LICENSE` — MIT

## Goals
- Provide a pattern for **confidential** smart contracts that work with Elements/Liquid's Confidential Transactions (CT).
- Demonstrate combining **multisig**, **timelock**, and **emergency-recovery** in a composable way using Simplicity.

## Limitations
- This is NOT production-ready. It MUST be reviewed, compiled, and formally verified before any use with real funds.
- Confidential TX handling (blinding, range proofs) remains in the transaction construction layer; Simplicity describes spending conditions rather than CT blinding operations.

If you'd like, I can:
- Try to compile or typecheck this locally (I cannot run external toolchains from here), or
- Help you set up a CI workflow (GitHub Actions) that runs `simplicityc` / `simplicityjs` to compile and run tests.

