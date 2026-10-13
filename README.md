# Nicolás Talero

**Software Architect & Web3 Security Researcher** · Founder @ [Digital Nova Solutions SAS](mailto:nicolastalero1108@gmail.com)

I build security tooling and audit smart contracts, with a focus on EVM-based protocols. My work centers on one problem that most automated audit tools ignore: **raw static-analysis output is noisy, and treating it as ground truth is how false positives end up in client reports.**

---

## What I actually do

I run smart contracts through a multi-tool audit process (Slither, Aderyn, Mythril, Semgrep, Heimdall, Echidna, Halmos) against real, deployed contracts — ICO-era tokens, vaults, multisig wallets, and DeFi protocols spanning 2016–present. The goal isn't the longest finding list; it's the **shortest list that's actually true**.

## Verified track record (real numbers, not vanity metrics)

- **50 contracts** scanned end-to-end — every single one documented, [50 individual reports, fully public](https://github.com/morfeo-1108/smart-contract-audit-archive/tree/master/reports/full-scan).
- **29 / 50 flagged with a Critical or High severity finding** in a category with real exploit potential: reentrancy, unchecked ERC20 transfers, `arbitrary-send-eth`, **delegatecall to a user-controlled address** (full contract takeover), weak PRNG, ETH locked with no withdraw path.
- Every finding is reported **after** a dedicated noise-filtering pass — detector-level style issues (`name-reused`, `naming-convention`, CI/CD linter noise) never make it into a severity count. (*The remaining 21 contracts split between medium-only, low-only, or genuinely clean — see the full archive for the exact breakdown. A clean result is a valid audit outcome, not a miss.*)

**Why the noise-filter matters:** I built it after catching, by manually reading the source, a report that scored `risk_label: CRITICAL` with "16 critical findings" — all 16 were the same Slither detector firing on duplicate OpenZeppelin import paths. Not a vulnerability.

That's the standard every number on this page is held to.

## Process

| Stage | What happens |
|---|---|
| **Static analysis** | Slither, Aderyn, Mythril, Semgrep (Solidity-scoped), Heimdall for unverified bytecode |
| **Cross-validation** | A finding only reaches HIGH confidence if corroborated by a second tool or a manual read of the real source |
| **Manual verification** | Anything claiming fund-theft, full-drain, or access-control bypass gets a live Foundry mainnet-fork test before it goes in a report |
| **Honest reporting** | "No exploitable vulnerability found" is a valid, useful audit outcome — reported as such, not padded |

## Capabilities beyond auditing

**Blockchain forensics & fund recovery intelligence** — multi-hop on-chain transaction tracing, mixer/bridge/exchange identification, and investigation of abandoned or trapped funds in historical contracts (2016–2020 era), using the Etherscan V2 multichain API and direct RPC verification. Example of the discipline applied: a real multisig cluster holding **~$9.78M** was fully traced — every one of the 30 associated owner addresses checked for on-chain activity, ENS registration, and public labels before concluding whether outreach was even viable. Real fund amounts, real verification, no claim made without on-chain proof.

**GPU / distributed inference infrastructure** — cost-aware routing between on-demand GPU inference and local fallback, with automatic warmup before a workload starts and cooldown immediately after, so compute cost tracks actual usage instead of running idle.

## Work with me

If you're a CTO, Web3 founder, or agency that needs an express triage audit, a deeper security review, or white-label audit support — reach out.

📧 **nicolastalero1108@gmail.com**

See [`smart-contract-audit-archive`](https://github.com/morfeo-1108/smart-contract-audit-archive) for real, verified audit examples.
