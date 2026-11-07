# NightWatch Demo Vault

Intentionally vulnerable Solidity smart vault deployed and verified on **Base Sepolia**.

## Deployed Contract
- **Contract Name:** `NightWatchDemoVault`
- **Network:** Base Sepolia (Chain ID `84532`)
- **Address:** [`0x70139e580853f6c54c976f027da3059f27e554ee`](https://sepolia.basescan.org/address/0x70139e580853f6c54c976f027da3059f27e554ee#code)
- **Deployment Transaction:** [`0x7e6a3354690e40033ae07111579f21ad37ca8aeeac4f23b2a53da8b98a20c061`](https://sepolia.basescan.org/tx/0x7e6a3354690e40033ae07111579f21ad37ca8aeeac4f23b2a53da8b98a20c061)

## Security Vulnerabilities for Auditing Demo
1. **Reentrancy:** `withdrawAll()` transfers ETH via low-level call before setting caller's balance to 0.
2. **Missing Access Control:** `setOwner()` allows any unprivileged caller to overwrite contract owner.
3. **tx.origin Authorization:** `emergencySweep()` authenticates via `tx.origin == owner`, exploitable via phishing proxy.

## Auto-Detection
NightWatch auto-detects this deployment via Foundry broadcast file in `broadcast/Deploy.s.sol/84532/run-latest.json`.
