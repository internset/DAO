# DIP-19: Ratify STPN Contract Ownership Transfer to a 2-of-3 Multisig, Confirm the Signers, Record the Cyberscope Audit, and Adopt a Signer Policy

**Author:** Niranjan Yadav, Founding Member, Internset DAO LLC
**Status:** Comment period
**Comment period:** [START DATE] to [END DATE] (7 days), in #dao-proposals on community.internset.com
**Vote type:** Signaling vote on Aragon (no on-chain actions)
**Aragon proposal:** TOKENVOTING-19 (link added when the vote opens)

---

## Summary

This proposal asks STPN holders to:

1. Ratify the transfer of STPN smart contract ownership from a single wallet to a 2-of-3 Safe multisig.
2. Confirm the three multisig signers, each an independent person holding their own key.
3. Record the independent Cyberscope audit of the STPN smart contract in the DAO's official records.
4. Adopt a Signer Policy that limits how the multisig may use its powers.

This is a signaling vote. Approving it does not move any tokens or funds and does not execute any transaction.

---

## Background

STPN is the utility and governance token of Internset DAO LLC, a Wyoming DAO LLC.

- Token contract (Polygon): [0x2Af618611967Ddfb05bC94d64cb6F4B523E10D36](https://polygonscan.com/token/0x2Af618611967Ddfb05bC94d64cb6F4B523E10D36)
- Deployed: 30 December 2024

The contract is built on OpenZeppelin libraries and includes an owner role that can pause and unpause token transfers. Until September 2026 this role was held by a single wallet, which the Cyberscope audit identified as a central point of risk. The contract has never been paused.

---

## 1. Ownership transfer to a 2-of-3 multisig

On 24 September 2026, ownership of the STPN contract was transferred to a Safe multisig. No tokens were moved; only the owner role changed.

| Item | Detail |
|---|---|
| Previous owner | 0x34F5a4657D686adC323FD25182C0570e519b1487 |
| New owner (Safe "Stipent Token Owner") | [0xDE4A956D470B2017543d844d36727d0C9B6494Bd](https://polygonscan.com/address/0xDE4A956D470B2017543d844d36727d0C9B6494Bd) |
| Threshold | Any 2 of 3 signers |
| Transaction | [0x3152e736…0e93766](https://polygonscan.com/tx/0x3152e736863a18ebd2d618acc7d29f729685a7353e9f5ca9b475c3aae0e93766) |
| Block | 94369095 (24 Sep 2026, 14:06 UTC) |

## 2. Multisig signers

The Safe was created with three keys held by the founding member while the other signers were onboarded. Two of those keys were then replaced, so that each signer is a separate person holding their own key.

| Signer | Name | Address | Added |
|---|---|---|---|
| 1 | Niranjan Yadav, Founding Member | 0x34F5a4657D686adC323FD25182C0570e519b1487 | Original signer |
| 2 | Samuel Mens | 0x2309762aAcA0a8F689463a42c0A6A84BE3A7ea51 | 29 Sep 2026, [0x46fccd37…408074](https://polygonscan.com/tx/0x46fccd37135abf3e72e0e590a8e80ae16e62d613bf5a23afd73962fab7408074) |
| 3 | Dr. Burzin Bharucha | 0xa74c5680c56caAa4ED1390303912bE1830a87C1B | 4 Oct 2026, [0xe2f87424…b78915](https://polygonscan.com/tx/0xe2f87424196caa1f3d67749ea6799732655745a66de4982f23d3435d29b78915) |

Each signer holds their own key and does not share it. Signer identities are verified through Cyberscope's KYC process. The Safe's full transaction history is public on PolygonScan; its only transactions to date are small setup tests, the two signer changes above, and one demonstration transfer of 0.2 POL to the company secretary.

## 3. Cyberscope audit

Cyberscope (a TAC Security company) audited the STPN smart contract. The report was published on 28 September 2026.

- Audit summary and report in the DAO repository: [github.com/internset/DAO/tree/main/audits](https://github.com/internset/DAO/tree/main/audits)
- Cyberscope audit page: [app.cyberscope.io/audits/stpn](https://app.cyberscope.io/audits/stpn)
- Report notarized on Polygon via Docuper: [transaction](https://polygonscan.com/tx/0x034abf0bed0ced11c3765408cbe7631e34169f04d665435059b6a8118987417c)

| Finding | Severity | Status |
|---|---|---|
| ST: Stops Transactions (owner can pause transfers) | Critical | Mitigated: owner is now the 2-of-3 multisig above |
| PFVOR: Permanent Freeze Via Ownership Renouncement | Minor | Acknowledged (see Signer Policy, rule 3) |
| L15: Local Scope Variable Shadowing | Minor | Acknowledged |
| L19: Stable Compiler Version | Minor | Acknowledged |

Checks passed: OTUT, ELFM, MT, BT and BC.

## 4. Signer Policy

If this DIP passes, the multisig signers agree to the following:

1. **Pause only for security.** The pause function may be used only in response to a genuine security threat, such as an exploit or a compromised key, never because of market conditions.
2. **Unpause promptly.** Any pause will be announced publicly with the reason and lifted as soon as the threat is resolved.
3. **No renouncing ownership.** Signers will not call renounceOwnership, as this could leave the contract permanently unable to recover from a pause.
4. **Major changes need a DAO vote.** Any token migration, change of contract owner, or change to this policy requires a DIP and an Aragon vote.
5. **Signer changes are disclosed.** Any change of signer or threshold will be announced publicly with the transaction hash and ratified in a later DIP.
6. **Independent judgment.** Each signer reviews every transaction independently before signing.

---

## Vote

- **Yes:** ratify items 1 to 3 and adopt the Signer Policy.
- **No:** do not ratify; the team will return with a revised proposal.
- **Abstain**

Per the DAO's governance settings, the vote requires participation of at least 15% of total STPN supply (1,500,000,000 STPN) and more than 50% approval of votes cast.

## References

- Operating Agreement of Internset DAO LLC, Sections 9.03 and 9.05
- Wyoming Amendment to Articles of Organization (Amendment ID 2025-005863581), Article VI
- DIP-18: Update DAO Resource Links (executed 1 October 2026)
- Stipent whitepaper: https://www.stipent.com/static-assets/documents/stipent-whitepaper.pdf
