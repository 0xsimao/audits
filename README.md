# Audits

Every security review published under this name: the report, and the
codebase it was performed on.

A folder per firm holds the reports; the two that ran both kinds of work
split theirs into `private-audits/` and `contests/`. `audit-codebases/`
holds one submodule per review, each a fork of the client's repository
pinned to the commit the review was performed at — the fork is what keeps
the code readable if the client's copy goes away, and the pin is what
keeps it the code that was read rather than the code as it is today.
Every fork also carries an `audit` branch and an `audited` tag at that
commit.

```sh
git clone --recurse-submodules https://github.com/0xsimao/audits
```

Or one review on its own:

```sh
git submodule update --init audit-codebases/<review>
```

## Reports

### Three Sigma — 23 private reviews

| Review | Date | Report | Published at |
|---|---|---|---|
| Maple Finance IV | 2024-11-26 | [2024-11-26-maple-finance-iv.pdf](Three%20Sigma/2024-11-26-maple-finance-iv.pdf) | [link](https://cdn.sanity.io/files/qoqld077/staging/a68d604be9eca467b1f656c2ca775e1cebc2a468.pdf) |
| Codeup | 2024-10-23 | [2024-10-23-codeup.pdf](Three%20Sigma/2024-10-23-codeup.pdf) | [link](https://cdn.sanity.io/files/qoqld077/staging/d9e57830a75b5165fd56e8b88037de7986a165ec.pdf) |
| Ojo Network | 2024-10-16 | [2024-10-16-ojo-network.pdf](Three%20Sigma/2024-10-16-ojo-network.pdf) | [link](https://cdn.sanity.io/files/qoqld077/staging/36dbe5ca76da3d2392bcee581548067705b8bd36.pdf) |
| Blast Ido Pools | 2024-08-07 | [2024-08-07-blast-ido-pools.pdf](Three%20Sigma/2024-08-07-blast-ido-pools.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/d2a7ca81740e715b604122c12dafbce599e43f2f.pdf) |
| Orange | 2024-07-15 | [2024-07-15-orange.pdf](Three%20Sigma/2024-07-15-orange.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/686ad4e1d5035d69002f5f97e281e3c5a8b7ce00.pdf) |
| Keyring II | 2024-07-10 | [2024-07-10-keyring-ii.pdf](Three%20Sigma/2024-07-10-keyring-ii.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/75b68b74f4b0dc6fbcd94892d934547d8259b57a.pdf) |
| Layer3 | 2024-07-06 | [2024-07-06-layer3.pdf](Three%20Sigma/2024-07-06-layer3.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/e8fbb07b1854347b8d87929e76703b00c28fd2c7.pdf) |
| Mitosis | 2024-06-25 | [2024-06-25-mitosis.pdf](Three%20Sigma/2024-06-25-mitosis.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/b6b3bd7bb47407d99e76abb7c6dc615c1db5018e.pdf) |
| DistrictOne | 2024-06-13 | [2024-06-13-districtone.pdf](Three%20Sigma/2024-06-13-districtone.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/fd2142f1d189dd29db23dff49d4018d4da9c01d6.pdf) |
| Maple Finance III | 2024-04-10 | [2024-04-10-maple-finance-iii.pdf](Three%20Sigma/2024-04-10-maple-finance-iii.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/36dbe5ca76da3d2392bcee581548067705b8bd36.pdf) |
| Metazero II | 2024-04-06 | [2024-04-06-metazero-ii.pdf](Three%20Sigma/2024-04-06-metazero-ii.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/3e07b0c2806b62578b8031e88c59bc5dbd38de1b.pdf) |
| Singularity | 2024-02-26 | [2024-02-26-singularity.pdf](Three%20Sigma/2024-02-26-singularity.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/45b8aac56a2b8e3b557df4329ac9bf8220b64012.pdf) |
| Ostium | 2024-02-19 | [2024-02-19-ostium.pdf](Three%20Sigma/2024-02-19-ostium.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/a95b9c69e0f65d1d6b0e649f0d62a362358ca8ce.pdf) |
| NFTPerp II | 2024-01-29 | [2024-01-29-nftperp-ii.pdf](Three%20Sigma/2024-01-29-nftperp-ii.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/87f617e82d5468500e950a669f30607376b37c32.pdf) |
| Metazero I | 2024-01-27 | [2024-01-27-metazero-i.pdf](Three%20Sigma/2024-01-27-metazero-i.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/1b1ab4ff365756fe1d86767f1e06744407570f5a.pdf) |
| Trestle | 2024-01-27 | [2024-01-27-metazero-i.pdf](Three%20Sigma/2024-01-27-metazero-i.pdf) (same file) | [link](https://cdn.sanity.io/files/qoqld077/production/1b1ab4ff365756fe1d86767f1e06744407570f5a.pdf) |
| M^0 | 2024-01-08 | [2024-01-08-m-0.pdf](Three%20Sigma/2024-01-08-m-0.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/1cdafafad874aba76e062ad8c216c98338c096db.pdf) |
| NftPerp I | 2024-01-02 | [2024-01-02-nftperp-i.pdf](Three%20Sigma/2024-01-02-nftperp-i.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/c19530de75e234ad15694b4563edb1fc9d2a3fd8.pdf) |
| Maple Finance II | 2023-11-16 | [2023-11-16-maple-finance-ii.pdf](Three%20Sigma/2023-11-16-maple-finance-ii.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/34f2311ad7e8315d043e23054e794c136f19a079.pdf) |
| Maple Finance | 2023-11-16 | [2024-10-16-ojo-network.pdf](Three%20Sigma/2024-10-16-ojo-network.pdf) (same file) | [link](https://cdn.sanity.io/files/qoqld077/staging/36dbe5ca76da3d2392bcee581548067705b8bd36.pdf) |
| Clip Finance I | 2023-11-10 | [2023-11-10-clip-finance-i.pdf](Three%20Sigma/2023-11-10-clip-finance-i.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/c23d04c8223879d2443221caf3ccb55ac118441a.pdf) |
| Glacier | 2023-07-12 | [2023-07-12-glacier.pdf](Three%20Sigma/2023-07-12-glacier.pdf) | [link](https://cdn.sanity.io/files/qoqld077/production/21bd3b6fa78c55968a6c9c7ea4fd49f34a8bd3d8.pdf) |
| Fuji Finance | 2023-05-06 | [2023-05-06-fuji-finance.pdf](Three%20Sigma/2023-05-06-fuji-finance.pdf) | [link](https://cdn.sanity.io/files/qoqld077/staging/32181a28eac3175d15fb8924d249bb0d91ca350c.pdf) |

### Sherlock — 13 private reviews, and 23 public competitions in [Sherlock/contests/](Sherlock/contests/)

| Review | Date | Report | Published at |
|---|---|---|---|
| Tenor | 2026-07-05 | [2026-07-05-tenor.pdf](Sherlock/private-audits/2026-07-05-tenor.pdf) | [link](https://github.com/tenor-labs/tenor-contracts/blob/main/audits/2026-07-Sherlock-review.pdf) |
| Morpho | 2026-06-10 | [2026-06-10-morpho.pdf](Sherlock/private-audits/2026-06-10-morpho.pdf) | [link](https://github.com/morpho-org/vault-v2/blob/main/audits/2026-07-08-gates-blackthorn.pdf) |
| ODEI | 2026-06-05 | [2026-06-05-odei.pdf](Sherlock/private-audits/2026-06-05-odei.pdf) | [link](https://github.com/sherlock-protocol/sherlock-reports/blob/main/audits/2026.06.16%20-%20Final%20-%20ODEI%20Collaborative%20Audit%20Report%201781625249.pdf) |
| Superfluid | 2026-01-13 | [2026-01-13-superfluid.pdf](Sherlock/private-audits/2026-01-13-superfluid.pdf) | [link](https://github.com/superfluid-org/protocol-monorepo/blob/dev/packages/ethereum-contracts/audits/2026-01-27%20-%20Final%20-%20Superfluid%20Collaborative%20Audit%20Report%201769517931.pdf) |
| Usual III | 2025-12-02 | [2025-12-02-usual-iii.pdf](Sherlock/private-audits/2025-12-02-usual-iii.pdf) | [link](https://drive.google.com/file/d/1knlIgoEGv5x33n9mhTLRqJe8T55r3HCy/view) |
| Maple Finance III | 2025-10-22 | [2025-10-22-maple-finance-iii.pdf](Sherlock/private-audits/2025-10-22-maple-finance-iii.pdf) | [link](https://github.com/maple-labs/maple-core-v2/blob/main/audits/2025-november/Sherlock-Maple-Finance-WM-Nov-2025.pdf) |
| Maple Finance II | 2025-09-08 | [2025-09-08-maple-finance-ii.pdf](Sherlock/private-audits/2025-09-08-maple-finance-ii.pdf) | [link](https://github.com/maple-labs/maple-core-v2/blob/main/audits/2025-sept-governor-timelock/Sherlock-Maple-Finance-timelock-Sept-2025.pdf) |
| Usual I | 2025-06-03 | [2025-06-03-usual-i.pdf](Sherlock/private-audits/2025-06-03-usual-i.pdf) | [link](https://1503334455-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FpUhQzPJGdJzuLTQ5sCym%2Fuploads%2F8gq6et5OGqJHJGphqav6%2FSherlock-%20Audit%20report%20on%20USD0%2B%2B%20upgrade%20(Burn%20Redemption%20Mechanism).pdf?alt=media&token=27674355-9c34-496e-970d-723f522221fa) |
| Beraborrow I | 2025-04-25 | [2025-04-25-beraborrow-i.pdf](Sherlock/private-audits/2025-04-25-beraborrow-i.pdf) | [link](https://1570492309-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FffzDCMBDa391vIMqruBP%2Fuploads%2FUKDtjc6Dkn6P6i35j5H1%2FManaged%20Leverage%20Vaults%20v0%20private%20audit%20Sherlock.pdf?alt=media&token=c7304efa-8040-4ed0-9a98-dc949af28a85) |
| Aegis | 2025-04-22 | [2025-04-22-aegis.pdf](Sherlock/private-audits/2025-04-22-aegis.pdf) | [link](https://github.com/sherlock-protocol/sherlock-reports/blob/main/audits/2025.04.26%20-%20Final%20-%20Aegis%20Collaborative%20Audit%20Report.pdf) |
| 1Inch | 2025-04-14 | [2025-04-14-1inch.pdf](Sherlock/private-audits/2025-04-14-1inch.pdf) | [link](https://github.com/1inch/1inch-audits/blob/master/Fees%20for%20LO%20and%20Fusion%20V1/Fee%20flow%20v1-Sherlock.pdf) |
| Gaib | 2025-03-28 | [2025-03-28-gaib.pdf](Sherlock/private-audits/2025-03-28-gaib.pdf) | [link](https://4221781861-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FLXNTW9blcTeiKZrMFhab%2Fuploads%2FQMsETA4dRNo2auiUSeOX%2FAIDa%20Vault%20Audit_20250411.pdf?alt=media&token=5e2f84ea-9698-4fa7-81ef-503771d234aa) |
| Nerite | 2025-02-03 | [2025-12-02-usual-iii.pdf](Sherlock/private-audits/2025-12-02-usual-iii.pdf) (same file) | [link](https://drive.google.com/file/d/1knlIgoEGv5x33n9mhTLRqJe8T55r3HCy/view) |

### 0xSimao — 5 private reviews

| Review | Date | Report | Published at |
|---|---|---|---|
| Spirit Protocol | 2025-11-28 | [2025-11-28-spirit-protocol.pdf](0xSimao/2025-11-28-spirit-protocol.pdf) | [link](https://github.com/0xSimao/audits/blob/main/2025-11-28-spirit-protocol.pdf) |
| Yieldoor III | 2025-06-23 | [2025-06-23-yieldoor-iii.pdf](0xSimao/2025-06-23-yieldoor-iii.pdf) | [link](https://github.com/0xSimao/audits/blob/main/2025-06-23-yieldoor.pdf) |
| Yieldoor II | 2025-06-20 | [2025-06-20-yieldoor-ii.pdf](0xSimao/2025-06-20-yieldoor-ii.pdf) | [link](https://github.com/0xSimao/audits/blob/main/2025-06-20-yieldoor.pdf) |
| Yieldoor I | 2025-05-12 | [2025-05-12-yieldoor-i.pdf](0xSimao/2025-05-12-yieldoor-i.pdf) | [link](https://github.com/0xSimao/audits/blob/main/2025-05-12-yieldoor.pdf) |
| Felix | 2025-03-14 | [2025-03-14-felix.pdf](0xSimao/2025-03-14-felix.pdf) | [link](https://github.com/0xSimao/audits/blob/main/2025-03-14-felix.pdf) |

### Blackthorn — 4 private reviews

| Review | Date | Report | Published at |
|---|---|---|---|
| Morpho Blue Bundles | 2026-07-14 | [2026-07-14-morpho-blue-bundles.pdf](Blackthorn/2026-07-14-morpho-blue-bundles.pdf) | [link](https://github.com/morpho-org/bundles/blob/main/audits/2026-07-06-blackthorn.pdf) |
| Tenor Markets | 2026-05-22 | [2026-05-22-tenor-markets.pdf](Blackthorn/2026-05-22-tenor-markets.pdf) | [link](https://github.com/tenor-labs/tenor-contracts/blob/main/audits/2026-06-Blackthorn-review.pdf) |
| Morpho Midnight | 2026-04-06 | [2026-04-06-morpho-midnight.pdf](Blackthorn/2026-04-06-morpho-midnight.pdf) | [link](https://github.com/morpho-org/midnight/blob/main/audits/2026-07-02-blackthorn.pdf) |
| Morpho Vault V2 | 2025-08-13 | [2025-08-13-morpho-vault-v2.pdf](Blackthorn/2025-08-13-morpho-vault-v2.pdf) | [link](https://github.com/morpho-org/vault-v2/blob/main/audits/2025-09-15-blackthorn.pdf) |

### Code4rena — 3 private reviews, and 14 public competitions in [Code4rena/contests/](Code4rena/contests/)

| Review | Date | Report | Published at |
|---|---|---|---|
| BendDAO | 2024-06-19 | [2024-06-19-benddao.md](Code4rena/private-audits/2024-06-19-benddao.md) | [link](https://code4rena.com/audits/2024-07-benddao-invitational) |
| INIT Capital I | 2024-01-26 | [2024-01-26-init-capital-i.md](Code4rena/private-audits/2024-01-26-init-capital-i.md) | [link](https://code4rena.com/reports/2024-01-init-capital-invitational) |
| INIT Capital II | 2023-12-15 | [2023-12-15-init-capital-ii.md](Code4rena/private-audits/2023-12-15-init-capital-ii.md) | [link](https://code4rena.com/reports/2023-12-initcapital) |

## Codebases

36 reviews whose codebase is open, each pinned to the
commit it was reviewed at.

| Review | Firm | Codebase | Reviewed at |
|---|---|---|---|
| Morpho Blue Bundles | Blackthorn | [morpho-org/bundles](https://github.com/morpho-org/bundles) | [`713af6ddfa`](https://github.com/0xsimao/bundles/tree/713af6ddfa64270c4ac8689532f05306a8ac72ea) |
| Morpho Midnight | Blackthorn | [morpho-org/midnight](https://github.com/morpho-org/midnight) | [`e9085f8c5f`](https://github.com/0xsimao/midnight/tree/e9085f8c5fe96df6e075847b95b0dd7cea86110d) |
| Superfluid | Sherlock | [superfluid-org/protocol-monorepo](https://github.com/superfluid-org/protocol-monorepo) | [`d69e4b0394`](https://github.com/0xsimao/protocol-monorepo/tree/d69e4b0394c38d2760b9b54f173a797b630c9ed1) |
| Morpho Vault V2 | Blackthorn | [morpho-org/vault-v2](https://github.com/morpho-org/vault-v2) | [`ce661d820f`](https://github.com/0xsimao/vault-v2/tree/ce661d820fb29307981f75eb42393db1c6e42758) |
| Cap | Sherlock | [sherlock-audit/2025-07-cap](https://github.com/sherlock-audit/2025-07-cap) | [`2bd34fa369`](https://github.com/0xsimao/2025-07-cap/tree/2bd34fa369d36af8ecc377090d3292ea74ccc669) |
| Symbiotic Relay | Sherlock | [sherlock-audit/2025-06-symbiotic-relay](https://github.com/sherlock-audit/2025-06-symbiotic-relay) | [`435a21fd81`](https://github.com/0xsimao/2025-06-symbiotic-relay/tree/435a21fd81bcd588439feef3108580f535b9e5eb) |
| Superfluid Locker System II | Sherlock | [sherlock-audit/2025-06-superfluid-locker-system](https://github.com/sherlock-audit/2025-06-superfluid-locker-system) | [`d8beaeed47`](https://github.com/0xsimao/2025-06-superfluid-locker-system/tree/d8beaeed47f766659a1600a87372a7905109aa3c) |
| Crestal Network | Sherlock | [sherlock-audit/2025-03-crestal-network](https://github.com/sherlock-audit/2025-03-crestal-network) | [`27a3c28155`](https://github.com/0xsimao/2025-03-crestal-network/tree/27a3c28155702b3a68f29347efedffb048010e33) |
| Symmio, Staking and Vesting | Sherlock | [sherlock-audit/2025-03-symm-io-stacking](https://github.com/sherlock-audit/2025-03-symm-io-stacking) | [`d7cf7fc96a`](https://github.com/0xsimao/2025-03-symm-io-stacking/tree/d7cf7fc96af1c25b53a7b500a98b411cd018c0d3) |
| Yieldoor | Sherlock | [sherlock-audit/2025-02-yieldoor](https://github.com/sherlock-audit/2025-02-yieldoor) | [`b5a0f779dc`](https://github.com/0xsimao/2025-02-yieldoor/tree/b5a0f779dce4236b02665606adb610099451a51a) |
| Autonomint | Sherlock | [sherlock-audit/2024-11-autonomint](https://github.com/sherlock-audit/2024-11-autonomint) | [`0d324e04d4`](https://github.com/0xsimao/2024-11-autonomint/tree/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b) |
| Superfluid Locker System | Sherlock | [sherlock-audit/2024-11-superfluid-locking-contract](https://github.com/sherlock-audit/2024-11-superfluid-locking-contract) | [`1fa5f86024`](https://github.com/0xsimao/2024-11-superfluid-locking-contract/tree/1fa5f86024be5f269e1a0898b1f939f1d4cce149) |
| Mento | Sherlock | [sherlock-audit/2024-10-mento-update](https://github.com/sherlock-audit/2024-10-mento-update) | [`098b17fb32`](https://github.com/0xsimao/2024-10-mento-update/tree/098b17fb32d294145a7f000d96917d13db8756cc) |
| Saffron Lido Vaults | Sherlock | [sherlock-audit/2024-08-saffron-finance](https://github.com/sherlock-audit/2024-08-saffron-finance) | [`38dd9c8436`](https://github.com/0xsimao/2024-08-saffron-finance/tree/38dd9c8436db341c331f1b14545770c1766fc0ee) |
| Flayer | Sherlock | [sherlock-audit/2024-08-flayer](https://github.com/sherlock-audit/2024-08-flayer) | [`0ec252cf9e`](https://github.com/0xsimao/2024-08-flayer/tree/0ec252cf9ef0f3470191dcf8318f6835f5ef688c) |
| Cork Protocol | Sherlock | [sherlock-audit/2024-08-cork-protocol](https://github.com/sherlock-audit/2024-08-cork-protocol) | [`db23bf67e4`](https://github.com/0xsimao/2024-08-cork-protocol/tree/db23bf67e45781b00ee6de5f6f23e621af16bd7e) |
| Winnables Raffles | Sherlock | [sherlock-audit/2024-08-winnables-raffles](https://github.com/sherlock-audit/2024-08-winnables-raffles) | [`81b28633d0`](https://github.com/0xsimao/2024-08-winnables-raffles/tree/81b28633d0f450e33a8b32976e17122418f5d47e) |
| Exactly Protocol Update - Staking Contract II | Sherlock | [sherlock-audit/2024-07-exactly-stacking-contracts](https://github.com/sherlock-audit/2024-07-exactly-stacking-contracts) | [`3eb87e3edf`](https://github.com/0xsimao/2024-07-exactly-stacking-contracts/tree/3eb87e3edf3bcd57c4cc1c6a73e8255f575b76de) |
| BendDAO | Code4rena | [code-423n4/2024-07-benddao](https://github.com/code-423n4/2024-07-benddao) | [`117ef61967`](https://github.com/0xsimao/2024-07-benddao/tree/117ef61967d4b318fc65170061c9577e674fffa1) |
| PoolTogether: The Prize Layer for DeFi | Sherlock | [sherlock-audit/2024-05-pooltogether](https://github.com/sherlock-audit/2024-05-pooltogether) | [`1aa1b8c028`](https://github.com/0xsimao/2024-05-pooltogether/tree/1aa1b8c028b659585e4c7a6b9b652fb075f86db3) |
| Arbitrum Bold | Code4rena | [code-423n4/2024-05-arbitrum-foundation](https://github.com/code-423n4/2024-05-arbitrum-foundation) | [`f6d314dc19`](https://github.com/0xsimao/2024-05-arbitrum-foundation/tree/f6d314dc19116c3bb7c744c4dda6db3fe8a37faf) |
| Renzo | Code4rena | [code-423n4/2024-04-renzo](https://github.com/code-423n4/2024-04-renzo) | [`519e518f2d`](https://github.com/0xsimao/2024-04-renzo/tree/519e518f2d8dec9acf6482b84a181e403070d22d) |
| Teller Finance | Sherlock | [sherlock-audit/2024-04-teller-finance](https://github.com/sherlock-audit/2024-04-teller-finance) | [`defe55469a`](https://github.com/0xsimao/2024-04-teller-finance/tree/defe55469a2576735af67483acf31d623e13592d) |
| TITLES Publishing Protocol | Sherlock | [sherlock-audit/2024-04-titles](https://github.com/sherlock-audit/2024-04-titles) | [`d7f60952df`](https://github.com/0xsimao/2024-04-titles/tree/d7f60952df22da00b772db5d3a8272a988546089) |
| Zivoe | Sherlock | [sherlock-audit/2024-03-zivoe](https://github.com/sherlock-audit/2024-03-zivoe) | [`d4111645b1`](https://github.com/0xsimao/2024-03-zivoe/tree/d4111645b19a1ad3ccc899bea073b6f19be04ccd) |
| Metazero II | Three Sigma | [metazerogg/stakingContract](https://github.com/metazerogg/stakingContract) | [`dffac73e83`](https://github.com/0xsimao/stakingContract/tree/dffac73e838a9fbd12bed18e41b9799177bcde7f) |
| M^0 | Three Sigma | [MZero-Labs/ttg](https://github.com/MZero-Labs/ttg) | [`a8127901fa`](https://github.com/0xsimao/ttg/tree/a8127901fa1f24a2e821cf4d9854a1aa6ac8088c) |
| INIT Capital II | Code4rena | [code-423n4/2023-12-initcapital](https://github.com/code-423n4/2023-12-initcapital) | [`a53e401529`](https://github.com/0xsimao/2023-12-initcapital/tree/a53e401529451b208095b3af11862984d0b32177) |
| veRWA | Code4rena | [code-423n4/2023-08-verwa](https://github.com/code-423n4/2023-08-verwa) | [`59add54eab`](https://github.com/0xsimao/2023-08-verwa/tree/59add54eab86f23b321e1d31eb2c7fb907eeb052) |
| Perennial V2 | Sherlock | [sherlock-audit/2023-07-perennial](https://github.com/sherlock-audit/2023-07-perennial) | [`120bcfef40`](https://github.com/0xsimao/2023-07-perennial/tree/120bcfef4028654de83477ffe992805ddada1043) |
| Tokemak | Sherlock | [sherlock-audit/2023-06-tokemak](https://github.com/sherlock-audit/2023-06-tokemak) | [`5d8e902ce3`](https://github.com/0xsimao/2023-06-tokemak/tree/5d8e902ce33981a6506b1b5fb979a084602c6c9a) |
| Ajna Protocol | Code4rena | [code-423n4/2023-05-ajna](https://github.com/code-423n4/2023-05-ajna) | [`07594e0751`](https://github.com/0xsimao/2023-05-ajna/tree/07594e07512692560109ac1a534dbcf38db2e72e) |
| zkSync Era System Contracts | Code4rena | [code-423n4/2023-03-zksync](https://github.com/code-423n4/2023-03-zksync) | [`21d9a364a4`](https://github.com/0xsimao/2023-03-zksync/tree/21d9a364a4a75adfa6f1e038232d8c0f39858a64) |
| Wenwin | Code4rena | [code-423n4/2023-03-wenwin](https://github.com/code-423n4/2023-03-wenwin) | [`91b89482aa`](https://github.com/0xsimao/2023-03-wenwin/tree/91b89482aaedf8b8feb73c771d11c257eed997e8) |
| Biconomy | Code4rena | [code-423n4/2023-01-biconomy](https://github.com/code-423n4/2023-01-biconomy) | [`8a7b05ac58`](https://github.com/0xsimao/2023-01-biconomy/tree/8a7b05ac58a65727e7e1fb17b91e418bc372be2b) |
| GoGoPool | Code4rena | [code-423n4/2022-12-gogopool](https://github.com/code-423n4/2022-12-gogopool) | [`aec9928d8b`](https://github.com/0xsimao/2022-12-gogopool/tree/aec9928d8bdce8a5a4efe45f54c39d4fc7313731) |
