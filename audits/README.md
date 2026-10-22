# Stipent (STPN) Security Audit Summaries

This document summarizes the security audits conducted on the Stipent (STPN) smart contract. STPN is the utility and governance token of Internset DAO LLC, deployed on the Polygon network. One independent audit has been performed by Cyberscope, a TAC Security company, to identify potential vulnerabilities and verify the security of the contract.

## Audit Summary

| Auditor | Report Date | Number of Findings | Critical | Medium | Minor / Informative |
|---|---|---|---|---|---|
| **Cyberscope** | September 28, 2026 | 4 | 1 | 0 | 3 |

---

## Cyberscope Audit Summary

Cyberscope conducted a security assessment of the Stipent (STPN) ERC-20 token contract deployed on Polygon.

### Scope

The audit focused on the following contract:

| Item | Detail |
|---|---|
| Contract | Stipent (STPN), ERC-20 |
| Network | Polygon |
| Address | [0x2Af618611967Ddfb05bC94d64cb6F4B523E10D36](https://polygonscan.com/token/0x2Af618611967Ddfb05bC94d64cb6F4B523E10D36) |

The contract is built on OpenZeppelin libraries and includes an owner role that can pause and unpause token transfers, and vote delegation for DAO governance.

### Findings

| Code | Finding | Severity | Status |
|---|---|---|---|
| ST | Stops Transactions | Critical | Mitigated: contract ownership was transferred to a 2-of-3 Safe multisig |
| PFVOR | Permanent Freeze Via Ownership Renouncement | Minor | Acknowledged |
| L15 | Local Scope Variable Shadowing | Minor | Acknowledged |
| L19 | Stable Compiler Version | Minor | Acknowledged |

### Checks passed

| Code | Description | Status |
|---|---|---|
| OTUT | Transfers User's Tokens | Passed |
| ELFM | Exceeds Fees Limit | Passed |
| MT | Mints Tokens | Passed |
| BT | Burns Tokens | Passed |
| BC | Blacklists Addresses | Passed |

Full descriptions, recommendations and the team's responses are in the report.

### Mitigation of the critical finding

On September 24, 2026, ownership of the STPN contract was transferred from a single wallet to a 2-of-3 Safe multisig, so no single key can pause transfers.

| Item | Detail |
|---|---|
| Contract owner (Safe) | [0xDE4A956D470B2017543d844d36727d0C9B6494Bd](https://polygonscan.com/address/0xDE4A956D470B2017543d844d36727d0C9B6494Bd) |
| Threshold | Any 2 of 3 signers |
| Ownership transfer | [View transaction on PolygonScan](https://polygonscan.com/tx/0x3152e736863a18ebd2d618acc7d29f729685a7353e9f5ca9b475c3aae0e93766) |

### Report

- Report in this repository: [2026-09-cyberscope-stpn-smart-contract-audit.pdf](2026-09-cyberscope-stpn-smart-contract-audit.pdf)
- Cyberscope audit page: [app.cyberscope.io/audits/stpn](https://app.cyberscope.io/audits/stpn)
- Cyberscope GitHub: [cyberscope-io/audits/stpn](https://github.com/cyberscope-io/audits/blob/main/stpn/audit.pdf)
- Notarized on Polygon via Docuper: [View transaction on PolygonScan](https://polygonscan.com/tx/0x034abf0bed0ced11c3765408cbe7631e34169f04d665435059b6a8118987417c)

---

## Disclaimer

*This summary is for informational purposes only and does not constitute financial or security advice. The full audit report should be consulted for detailed information. The audit findings and remediation efforts reflect the state of the contract at the time of the audit.*
