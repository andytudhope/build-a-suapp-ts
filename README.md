# Build a SUAPP with Typescript

This is a starter template for applications on SUAVE which use typescript for their frontends. 

It comes with minimal dependencies. It is intended to demonstrate how to create Confidential Compute Requests, send them, and handle any responses.

## Get Started

First, you need to build [`suave-viem`](https://github.com/flashbots/suave-viem). Clone that repo and then use [`bun`](https://bun.sh/) to do the following:

```bash
$ cd suave-viem
$ bun install
$ bun run build
$ cd src/ && bun link
```

Clone this repo and set up the submodules required by `forge` for your smart contracts:

```bash
$ git clone git@github.com:andytudhope/build-a-suapp-ts. suapp-ts
$ cd suapp-ts
$ git submodule init
$ git submodule update
```

Use `bun` to install your dependencies and link `suave-viem`:

```bash
$ bun install
$ bun link viem
```

Compile your contracts with:

```bash
$ bun run compile
```

Start the frontend with:

```bash
$ bun run dev
```

## Notes

1. Confidential Compute Requests (CCRs) on SUAVE do not work with wallets that implements the EIP-1193 Javascript API. Therefore, we use the unsafe `eth_sign` method to sign CCRs, which does work, but requires that you enable this functionality in wallets like MetaMask.
    1. To do so in MetaMask, go to "Settings" -> "Advanced" -> scroll to bottom -> switch Eth_sign requests on.
2. This template assumes that you are running SUAVE locally and have your browser wallet connected to `localhost:8545`.
3. No tests are included in `forge`, as it is not trivial to test new precompiles and different transaction types (i.e. CCRs) in `forge` at this time.