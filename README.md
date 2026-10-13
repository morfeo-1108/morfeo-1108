# Nicolás Talero

**Software Architect & Web3 Security Researcher** · Founder @ [Digital Nova Solutions SAS](mailto:nicolastalero1108@gmail.com)

I build security tooling and audit smart contracts, with a focus on EVM-based protocols. My work centers on one problem that most automated audit tools ignore: **raw static-analysis output is noisy, and treating it as ground truth is how false positives end up in client reports.**

---

## What I actually do

I run an internal multi-tool audit pipeline (Slither, Aderyn, Mythril, Semgrep, Heimdall, Echidna, Halmos, plus an in-house LLM review layer) against real, deployed contracts — ICO-era tokens, vaults, multisig wallets, and DeFi protocols spanning 2016–2024. The pipeline's job isn't to produce the longest finding list; it's to produce the **shortest list that's actually true**.

## Verified track record (real numbers, not vanity metrics)

- **50 contracts** scanned end-to-end through the full tool pipeline — every single one documented, [50 individual reports, fully public](https://github.com/morfeo-1108/smart-contract-audit-archive/tree/master/reports/full-scan).
- **29 / 50 flagged with a Critical or High severity finding** in a category with real exploit potential: reentrancy, unchecked ERC20 transfers, `arbitrary-send-eth`, **delegatecall to a user-controlled address** (full contract takeover), weak PRNG, ETH locked with no withdraw path.
- Every finding is reported **after** a dedicated noise-filtering pass — detector-level style issues (`name-reused`, `naming-convention`, CI/CD linter noise) never make it into a severity count. (*The remaining 21 contracts split between medium-only, low-only, or genuinely clean — see the full archive for the exact breakdown. A clean result is a valid audit outcome, not a miss.*)

**Why the noise-filter matters:** I built it after catching, by manually reading the source, a report that scored `risk_label: CRITICAL` with "16 critical findings" — all 16 were the same Slither detector firing on duplicate OpenZeppelin import paths. Not a vulnerability. I also built an **identifier-grounding check** after an LLM-generated finding referenced a contract field that didn't exist in the real source — every named identifier now gets checked against the actual code before a finding ships above LOW confidence.

That's the standard every number on this page is held to.

## Ecosystems & active work

| Area | What it is | Stack / notes |
|---|---|---|
| **Web3 Audit Pipeline** | Multi-tool smart contract audit orchestration with cross-validation before any finding is trusted | Slither, Aderyn, Mythril, Semgrep, Heimdall, Echidna, Halmos, custom LLM review |
| **On-chain Fund Recovery Research** | Identifying genuinely abandoned/trapped funds in historical contracts (2016–2020 era), with on-chain verification discipline before any claim is made | Etherscan V2 multichain API, direct RPC verification, Foundry fork testing for exploit confirmation |
| **AI-driven Fiscal Intelligence Platform** | Large-scale data platform for tax/financial intelligence | In development |
| **Edge AI Nodes** | Distributed inference infrastructure | In development |

## Methodology, briefly

1. Static analysis (Slither/Aderyn/Mythril/Semgrep) — never trusted raw.
2. Cross-validation — a finding only reaches HIGH confidence if corroborated across tools or verified manually against the real source.
3. Manual verification for anything claiming fund-theft or full-drain potential — including, when it matters, a live Foundry mainnet-fork test before anything goes in a report.
4. Honest reporting of negative results. "No exploitable vulnerability found" is a valid, useful audit outcome.

## Work with me

If you're a CTO, Web3 founder, or agency that needs an express triage audit, a deeper security review, or white-label audit support — reach out.

📧 **nicolastalero1108@gmail.com**

See [`smart-contract-audit-archive`](https://github.com/morfeo-1108/smart-contract-audit-archive) for real, verified audit examples.
