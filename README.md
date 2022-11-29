# Interchain security Chain Information
Welcome to Interchain security Game of Chains testnet!

Contents

* [Status](#status)
* [Chain Data](#chain-data)

## Status

* Timeline
  * 2022-12-02: Spawn time: `2022-12-01T17:00:00.000000000Z`
  * 2022-12-02: Proposal 34 voting period ends
  * 2022-11-29: Proposal 34 goes into voting period
  * 2022-11-29: Genesis file without CCV state is generated

Interchain security will launch as a consumer chain through a governance proposal in the `provider` chain. Read the [Consumer Chain Start Process](https://github.com/hyphacoop/ics-testnets/blob/main/docs/Consumer-Chain-Start-Process.md#consumer-chain-start-process) page for more details about the workflow.

The following items will be included in the proposal:
* Genesis file hash
  * The SHA256 is used to verify against the genesis file that the proposer has made available for review.
  * This "fresh" genesis file cannot be used to run the chain: it must be updated with the CCV states after the spawn time is reached.
* Binary hash
* Spawn time
  * Even if the proposal passes, the CCV states will not be available from the provider chain until after the spawn time is reached.

## Chain Data

### Downloading the binary

[Interchain security](https://github.com/oopcode/interchain-security) v1.0.0 binaries are [available for download](https://github.com/p2p-org/ics-testnets-interchain-security/releases/tag/v1.0.0).

### Building from source

Steps to build:
```
docker run --rm -ti -v /<your_local_volume>:/app --entrypoint /bin/bash ghcr.io/strangelove-ventures/checksum:v.0.1.0
cd /app/
git clone https://github.com/oopcode/interchain-security.git
cd interchain-security/
git checkout v1.0.0
make build       
sha256sum /interchain-security-cdd
6ea06412c306ccb9d37437754fa76b0c66f0d13edfe1d9d25f5b7e460a2eb1df  /interchain-security-cdd
```

The binary will output to `/interchain-security-cdd`, with sha256 checksum `6ea06412c306ccb9d37437754fa76b0c66f0d13edfe1d9d25f5b7e460a2eb1df`.

### Genesis file

**The genesis file for Interchain Security consumer chains must include the CCV (Cross Chain Validation) state generated by the provider chain _after_ the spawn time is reached.**

Fresh genesis file **without CCV state**: **[genesis.json](genesis.json)** SHA256 hash sum: `975789311bc4919a867be8bf4c2fcbe838a9c7565c66c523280e2cc817339a8a`

The genesis file with was generated using the following settings:

* Chain ID: `liquidity`
* Denom: `stake`
* Signed blocks window: `"8640"`

