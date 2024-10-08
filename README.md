# Solana Safe Transfer

A safer way to transfer Solana tokens, the app will ask users to provide a confirmation code in addition to the wallet
address before transferring tokens.

[Live Demo on Devnet](https://solana-safe-transfer-web.vercel.app)

## tl;dr

To run both the front-end and the on-cin parts locally, check the readme file inside the anchor repo first [solana-safe-transfer-anchor](https://github.com/MohammedAlabd/solana-safe-transfer-anchor) and after deploying your on-chain app, you can check the readme file inside [solana-safe-transfer-web](https://github.com/MohammedAlabd/solana-safe-transfer-web) and folloe the steps to get the front-end of the app running

## How to run the two apps

First you will need to clone the repo

```bash
git clone --recurse-submodules git@github.com:MohammedAlabd/solana-safe-transfer.git
```

Then you can go ahead and build the program, deploy it, and then run the front-end app

### on-chain app

- Get into the app repo

```bash
cd solana-safe-transfer-anchor
```

- Update the program key

```bash
anchor keys sync
```

- build the program

```bash
anchor build
```

- run a local validator

```bash
solana-test-validator
```

- Deploy the program

```bash
anchor deploy
```

### web app

- Get into the app repo

```bash
cd solana-safe-transfer-web
```

- install dependencies

```bash
bun install
```

- Create a .env file

```bash
cp .env.example .env
```

- Update the env var `NEXT_PUBLIC_SOLANA_RPC_URL` with the right value. Notice that you can also leave that pointing to
  devnet since I already have a devenet program deployed under the address that is in the code

- if you want to deploy your own program, make sure to copy the idl file from the anchor repo
  `target/idl/solana_safe_transfer.json` to the `src/programs/solana-safe-transfer` folder under the name `idl.json`.
  And the file `target/types/solana_safe_transfer.ts` to the `src/programs/solana-safe-transfer` folder under the name
  `types.ts` after building the anchor program

- run the app

```bash
bun dev
```
