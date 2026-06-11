Algorithmic Stablecoin Built on Market Arbitrage, Debt Claims & Protocol Treasury
Release Date: 2026

Abstract
USDH is a decentralized algorithmic stablecoin protocol supported by three core modules: market arbitrage regulation, yUSD debt claim buffer, and protocol treasury repayment system. The protocol issues three native on-chain tokens:
USDH: USD-pegged stablecoin
WEI: Native utility and governance token of the protocol
yUSD: Protocol debt token
In the normal price band of 0.9 < USDH < 1.1, a dual-token arbitrage mechanism similar to UST-LUNA maintains the peg. When USDH trades above 1.1, progressive mint taxes are imposed to fill the treasury pool and pull the price back to the target range. If USDH falls below 0.9, burned USDH is converted partially into WEI and partially into yUSD debt tokens for the discounted value gap. This design avoids infinite WEI minting and the classic death spiral of early algorithmic stablecoins.
Treasury funds accumulated via arbitrage taxes, protocol fees and yield strategies are exclusively used to repurchase yUSD and cover interest payments for debt holders. Version v0.1 adds a comprehensive on-chain risk control framework to mitigate systemic risks, including bank run prevention, flash loan attack defense, whale long/short manipulation limits, oracle failure safeguards, daily transaction caps, and tiered circuit breakers. All risk rules are hard-coded in smart contracts to create multi-layer safety barriers for long-term peg stability.

1 Project Background & Core Design Goals
1.1 Industry Pain Points
Traditional dual-token algorithmic stablecoins suffer from inherent structural vulnerabilities:
De-pegging triggers mass stablecoin burning and unlimited equity token minting, forming a self-reinforcing death spiral;
No debt buffer mechanism to absorb discount pressure during deep de-pegging events;
No dedicated treasury reserve for debt redemption and interest compensation;
Absence of native on-chain risk controls: unregulated mass redemptions, flash loan manipulation, whale market control, and single-source oracle failure risks.
1.2 Core Design Objectives
Peg Stability: Maintain USDH price steadily within the 0.9–1.1 USD target band;
Death Spiral Resistance: Convert discount gaps to yUSD debt instead of excessive WEI issuance during deep de-pegging;
Sustainable Treasury Operation: Build a self-replenishing treasury pool for yUSD buybacks and interest disbursement;
Full On-Chain Risk Mitigation: Prevent bank runs, flash loan exploits, whale manipulation and oracle price distortion via hard-coded contract rules;
Decentralized Transparency: All mint, burn, tax, treasury and risk control operations are fully traceable and auditable on-chain;
Community Governance: All critical parameters are adjustable only via WEI token voting with time-lock delays.
2 Native Token Ecosystem
Three interoperable native tokens serve distinct roles within the closed-loop economic system.
2.1 USDH: USD-Pegged Stablecoin
Core utility: Medium of exchange, unit of account and store of value pegged to 1 USD;
Supply dynamics: Minted or burned algorithmically via arbitrage operations;
Target trading band: 0.9 < USDH < 1.1.
2.2 WEI: Protocol Native Equity & Governance Token
Core utility: Governance voting, arbitrage swap medium, fee payment carrier, treasury reserve asset;
Value capture sources: Arbitrage tax revenue, protocol transaction fees, treasury yield gains, ecosystem adoption.
2.3 yUSD: Protocol Debt Claim Token
Core definition: On-chain debt certificate issued to absorb price discounts when USDH < 0.9;
Generation logic: Burned USDH yields WEI equal to the real-time oracle price value, while the 1 USD value gap is minted as yUSD;
Repayment guarantee: Fully backed by treasury assets, with structured linear vesting and interest distribution rules.
3 Market Arbitrage Stabilization Module
All swap logic executes automatically via smart contracts based on decentralized oracle price feeds, split into three independent price bands.
3.1 Normal Band: 0.9 < USDH < 1.1
A bidirectional arbitrage mechanism analogous to the UST-LUNA model operates without additional taxation or debt issuance:
When USDH > 1.0: Users burn WEI to mint USDH, increasing USDH supply to suppress overvaluation;
When USDH < 1.0: Users burn USDH to mint WEI, reducing USDH circulating supply to lift undervaluation.
3.2 Premium Band: USDH > 1.1
A progressive taxation mechanism activates to curb excessive minting arbitrage:
Users may still burn WEI to mint USDH, but progressive taxes scale upward with the USDH premium;
All tax revenue is transferred directly to the protocol treasury with zero re-entry into public circulation;
Tax burden raises arbitrage costs and restrains speculative over-minting to push prices back under 1.1.
3.3 Deep Discount Band: 0 < USDH < 0.9 (Core Anti-Death-Spiral Innovation)
To avoid massive WEI inflation during severe de-pegging, discounted value gaps are converted to yUSD debt tokens:
Formula for swap output after burning 1 USDH at oracle price P:
Received WEI amount = Burned USDH Quantity × Real-Time Price P
Minted yUSD amount = Burned USDH Quantity × (1 − P)
Example: At a USDH price of 0.8, burning 1 USDH yields 0.8 USD worth of WEI plus 0.2 yUSD debt tokens;
System benefits: WEI supply expansion is drastically limited to halt panic-driven death spirals; mass USDH burning reduces circulating supply rapidly to facilitate peg recovery; price pressure is deferred as time-dated treasury debt.
4 yUSD Debt Token Mechanism
4.1 Debt Generation Triggers
yUSD is minted exclusively when the oracle feed reports USDH price below 0.9 during user USDH burn operations. All minting logic is automated on-chain without manual intervention.
4.2 Vesting & Repayment Rules
Initial Lock-Up: Newly minted yUSD enters a mandatory lock-up period (configurable 7–30 days via governance);
Linear Vesting Schedule: After lock-up expiration, yUSD unlocks linearly over a 90–180 day window to avoid concentrated sell-off pressure;
Interest Structure: Holders earn fixed annual interest (5%–15% APR, adjustable via community vote) compensated from treasury income;
Repayment Priority: Treasury assets redeem the earliest-matured yUSD first at face value (1 yUSD = 1 USD equivalent), and redeemed yUSD is permanently burned;
Secondary Market Liquidity: yUSD is transferable and tradable on decentralized exchanges; market prices reflect treasury solvency and peg recovery expectations.
5 Protocol Treasury Module
The treasury acts as the protocol’s central reserve pool, responsible for debt redemption, interest payouts, market intervention and ecosystem development.
5.1 Treasury Revenue Streams
Progressive mint taxes collected when USDH trades above 1.1;
Protocol transaction, swap and arbitrage fees generated across the ecosystem;
Low-risk on-chain yield farming and liquidity management gains;
A fixed share of arbitrage seigniorage collected during normal-band operations;
Ecosystem grants and community donations.
5.2 Mandatory Treasury Allocation Rules
Fund disbursement ratios are hard-coded and only modifiable via WEI governance with a 48-hour time lock:
70% Priority Allocation: Cover principal and interest payments for outstanding yUSD debt;
20% Market Stabilization Fund: On-chain market intervention to defend the USDH peg during volatility;
10% Ecosystem & Emergency Reserve: Security audits, ecosystem incentives and crisis contingency capital.
All treasury withdrawals require multi-signature validation and time-lock delays, with every fund movement recorded permanently on-chain for full auditability.
5.3 Solvency Safeguards
Mandatory minimum coverage ratio: Treasury total assets / Unrepaid yUSD principal ≥ 120%;
Automatic revenue boost trigger: If coverage ratio drops below 120%, tax rates and protocol fees increase automatically to accelerate treasury accumulation;
Surplus distribution: When coverage ratio exceeds 150%, governance may vote to allocate excess funds to WEI buyback-and-burn or reduce protocol tax burdens.
6 Closed-Loop Economic Logic
6.1 Positive Feedback Loop (Stable Market Conditions)
Stable USDH peg → expanded ecosystem adoption → rising tax & fee revenue → growing treasury reserves → improved yUSD repayment capacity → stronger market confidence → reinforced USDH price stability → increased WEI token value capture.
6.2 Risk Isolation Logic (Contrasted Against Classic Algorithmic Stablecoins)
Traditional dual-token model: Deep de-pegging → unlimited WEI minting → WEI price collapse → further USDH de-pegging (unstoppable death spiral);
USDH protocol model: Deep de-pegging → discount gaps converted to yUSD debt → controlled WEI issuance → treasury-managed scheduled debt repayment → gradual peg recovery → closed-loop debt resolution.
7 Technical Architecture
7.1 Underlying Blockchain Compatibility
Built for EVM-compatible blockchains (Ethereum, BSC, Polygon and cross-chain deployments). The full smart contract suite includes:
Arbitrage Swap Contract, Tax Distribution Contract, yUSD Debt Contract, Treasury Management Contract, Oracle Adapter, Governance Contract, Global Risk Control Contract, Circuit Breaker Controller, Transaction Limit Manager, Flash Loan Detection Contract.
All arbitrage mint/burn operations pass through the risk control contract for sequential validation; any failed risk check reverts the transaction entirely.
7.2 Decentralized Oracle Infrastructure
Multi-source independent price feeds integrated (Chainlink and custom oracle node networks);
Price sampling interval: 15 minutes per feed update;
Built-in filters for abnormal price spikes, feed downtime protection and fallback price logic.
7.3 Base Security Design
Full open-source contract code with mandatory third-party security audits before mainnet launch;
Critical parameter changes require governance voting and time-lock delays;
Emergency pause circuit breaker for extreme systemic risk scenarios;
Complete treasury asset isolation to eliminate unauthorized fund withdrawals.
8 Full On-Chain Risk Control Framework
All risk control rules are permanently encoded in smart contracts. Core parameters may only be adjusted via WEI token governance votes with a minimum 48-hour time lock. Every limit trigger, transaction block and circuit breaker activation emits verifiable on-chain events. The framework contains six independent sub-systems: bank run prevention, flash loan defense, whale long/short restriction, oracle failure protection, tiered circuit breakers, and dual-layer address/global transaction caps.
8.1 Bank Run Prevention System (Mitigate Mass Panic Redemptions)
Bank runs are defined as synchronized mass USDH burn operations that trigger rapid WEI supply expansion and intensified de-pegging pressure.
8.1.1 Sliding Window Burn Limits
Dual sliding tracking windows: 1-hour and 24-hour burn volume counters per wallet address;
1-hour single-address burn cap: Max 30% of the address’s total held USDH balance;
24-hour single-address burn cap: Max 60% of the address’s total held USDH balance;
Global 24-hour burn hard cap: Capped at 15% of total circulating USDH supply. The burn channel closes automatically once the cap is reached, resetting daily at UTC rollover.
8.1.2 Discount Band Burn Attenuation Coefficient
When USDH < 0.9 (debt issuance mode), additional burn frequency limits apply:
A minimum 5-minute cooldown is enforced between consecutive burn transactions from one address;
Continuous repeated burns trigger a 20% reduction in swap output volume per subsequent transaction; full limits restore after a 10-minute cooling period.
8.1.3 Run Early Warning & Treasury Buffer Pool
The risk contract triggers an on-chain warning if 1-hour global burn volume exceeds 80% of the daily global cap;
A dedicated treasury buffer sub-pool automatically releases WEI to secondary markets to absorb sell pressure during warning states;
Level 1 circuit breaker activates temporarily halting all burns for 2 hours if 1-hour burn volume hits 95% of the global cap.
8.2 Flash Loan Attack Defense System
Flash loan exploits enable attackers to borrow large capital within a single block to manipulate oracle prices or extract arbitrage profits, then repay loans before block confirmation with zero permanent capital exposure.
8.2.1 Prior Block Holding Validation
All USDH/WEI mint/burn swaps validate asset block timestamps: tokens used for arbitrage must be held in the wallet from the previous block. Assets transferred or borrowed within the current block via flash loans cannot execute swap operations.
Validation logic: tokenTransferBlockNumber < currentBlockNumber
8.2.2 Single-Block Transaction Volume Caps
Per-address single-block mint/burn limit: Maximum 0.1% of total protocol circulating supply;
Global single-block swap hard cap. All pending swap transactions within the block revert once the ceiling is hit.
8.2.3 Flash Loan Origin Address Interception
Integrates interfaces with mainstream lending protocols to tag transactions originating from flash loan contract addresses; all swap requests initiated by tagged flash loan contracts are automatically rejected.
8.2.4 Multi-Block Price Confirmation Rule
Oracle prices require consistent readings across three consecutive blocks to qualify as valid swap pricing benchmarks. Temporary single-block price spikes cannot trigger mint or burn execution.
8.3 Whale Long & Short Manipulation Restrictions
Mitigate market control by large holders executing one-sided massive arbitrage operations.
8.3.1 Long Position Restrictions (Mass WEI Burn to Mint USDH for Price Pumping)
24-hour single-address USDH mint cap: Max 50% of the address’s total WEI market value;
Stricter limits during premium band (USDH > 1.1): Mint quotas halved with elevated progressive tax rates;
Per-address USDH holding ceiling: No wallet may hold more than 5% of total circulating USDH; new mint operations are blocked once this threshold is crossed.
8.3.2 Short Position Restrictions (Mass USDH Burn to Crash Peg Price)
Wallets holding over 3% of circulating USDH are marked as whale addresses, with burn quotas reduced by 50%;
Discount band (USDH < 0.9) whale burn transactions incur an additional 10% swap fee to raise shorting costs;
On-chain monitoring flags sequential large sell orders across decentralized exchanges linked to the same whale address, activating further burn throttling.
8.3.3 Tiered Holding Weight Restrictions
Address holding <1% total supply: Standard unrestricted transaction quotas;
1% ≤ Holding <3%: Swap limits multiplied by 0.7;
3% ≤ Holding <5%: Swap limits multiplied by 0.5;
Holding ≥5%: All arbitrage mint/burn functions suspended (secondary market spot trading remains permitted).
8.4 Oracle Failure & False Price Protection Suite
Mitigate risks from malicious feed nodes, network outages, single-source price flash crashes and erroneous pricing triggering incorrect arbitrage execution.
8.4.1 Multi-Source Median Price Calculation
A minimum of three independent oracle data feeds are integrated. The contract discards the highest and lowest outlier values and uses the median price as the official swap benchmark.
8.4.2 Inter-Period Price Volatility Filter
Any price swing exceeding ±8% between consecutive oracle updates is marked as a spike and discarded;
A unilateral price shift exceeding 20% within one hour triggers an oracle warning state, temporarily pausing arbitrage swaps until pricing stabilizes.
8.4.3 Oracle Node Health Monitoring
Any feed node returning five consecutive off-median or time-out readings is automatically removed from the active feed set;
Governance proposals are triggered on-chain if a single oracle feed remains offline for over 30 minutes to prompt node replacement votes.
8.4.5 Historical Price Fallback Mechanism
If fewer than two valid oracle feeds remain operational, the contract switches to a 72-hour sliding average historical price for swap calculations. Real-time price-driven arbitrage is suspended to avoid damage from invalid spot pricing.
8.5 Tiered Circuit Breaker Mechanism
Three trigger tiers activate automatic market isolation rules based on median oracle prices, with zero manual operator control. All restrictions lift automatically once prices return to stable bands and maintain the threshold for a defined duration.
Stable target band: 0.9 ≤ USDH ≤ 1.1
Level 1 Circuit Breaker (Warning Restriction – Mild De-Pegging)
Trigger Condition: USDH > 1.15 OR USDH < 0.85
Enforced Rules:
All mint/burn quotas reduced to 50% of baseline limits;
Premium tax rates increased by 5%, discount band swap fees raised by 3%;
Automated small-scale treasury market intervention activates hourly to stabilize prices.
Lift Condition: Price returns to the 0.92–1.08 range and persists for 30 consecutive minutes.
Level 2 Circuit Breaker (Hard Restriction – Moderate De-Pegging)
Trigger Condition: USDH > 1.20 OR USDH < 0.80
Enforced Rules:
Unilateral swap channel closure: Minting USDH suspended during severe premiums; burning USDH suspended during severe discounts;
Global 24-hour swap ceiling reduced to 30% of standard volume;
All whale address arbitrage permissions revoked, only retail small-volume swaps permitted;
Treasury deploys expanded intervention capital to restore peg stability.
Lift Condition: Price recovers to Level 1 breaker range and holds for 1 continuous hour.
Level 3 Circuit Breaker (Global Emergency Halt – Systemic Crisis)
Trigger Condition: USDH > 1.30 OR USDH < 0.70, OR fewer than two active valid oracle feeds
Enforced Rules:
Complete suspension of all bidirectional USDH-WEI mint/burn arbitrage swaps;
yUSD lock-up, vesting and treasury redemption functions remain fully operational to protect debt holder claims;
Multi-signed emergency treasury fund pool deployed for large-scale secondary market intervention;
On-chain emergency governance voting channel opens for parameter adjustment or swap resumption proposals.
Lift Condition: USDH price recovers to the 0.9–1.1 stable band, all oracle feeds restore valid data, and a governance vote approves circuit breaker deactivation.
8.6 Dual-Layer Transaction Caps: Per-Wallet & Global Protocol Limits
All swap transactions validate against address quotas first, then global protocol ceilings; transactions revert automatically if either cap is exceeded.
8.6.1 Per-Address Time-Series Caps (Governance Configurable Baselines)
Single-block cap: Mint/burn volume ≤ 0.1% of the wallet’s total asset value;
1-hour sliding cap: Mint/burn volume ≤ 30% of the wallet’s total asset value;
24-hour sliding cap: Mint/burn volume ≤ 60% of the wallet’s total asset value;
Additional attenuation coefficients for whale addresses as defined in Section 8.3.3.
8.6.2 Global Protocol Daily Hard Caps
Maximum daily USDH mint volume: 15% of total circulating USDH supply;
Maximum daily USDH burn volume: 15% of total circulating USDH supply;
Single-block global swap ceiling: 0.5% of total protocol circulating supply.
Caps reset daily at UTC block rollover once hit.
8.6.7 Supplementary yUSD Risk Caps
Per-address unredeemed yUSD holding ceiling: Max 8% of total outstanding yUSD supply to prevent concentrated mass redemptions draining treasury reserves;
Daily treasury yUSD redemption volume cap to smooth repayment outflow and avoid sudden treasury liquidity depletion.
8.7 Malicious Address Monitoring & Transaction Throttling (Backstop Risk Control)
Automated on-chain tagging for wallets exhibiting repeated limit violations, frequent flash loan contract interaction, and sequential large-scale manipulative trading patterns;
Tagged restricted addresses receive an additional 50% swap quota reduction and doubled swap fees;
Governance vote with time lock required to permanently blacklist confirmed malicious exploit addresses; blacklisted wallets retain full asset ownership and secondary transfer functionality but lose arbitrage mint/burn privileges to balance decentralization and security;
The blacklist storage layer is fully on-chain, with every add/remove action permanently auditable; project core teams lack unilateral authority to modify the list without community approval.
9 Comprehensive Risk Analysis & Mitigation Matrix
9.1 Oracle Price Distortion / Feed Collapse Risk
Mitigations: Multi-source median pricing, inter-period volatility filtering, three-block price confirmation logic, historical fallback pricing, automatic removal of offline feed nodes, tiered circuit breaker swap suspension.
9.2 Bank Run & Panic Mass Redemption Risk
Mitigations: Sliding-window burn limits, global daily burn hard cap, discount band swap attenuation coefficients, treasury run buffer pool, Level 1 circuit breaker throttling.
9.3 Single-Block Flash Loan Manipulation Risk
Mitigations: Prior-block asset holding validation, single-block volume caps, flash loan contract address interception, multi-block oracle price confirmation rule.
9.4 Whale One-Sided Long/Short Market Control Risk
Mitigations: Tiered per-address holding quotas, whale swap volume attenuation, differentiated premium/discount swap fee surcharges, maximum single-wallet USDH holding ceiling.
9.5 Extreme Volatility Systemic Collapse Risk
Mitigations: Three-stage tiered circuit breakers with graduated market isolation, phased treasury intervention capital deployment, gradual volume restriction escalation.
9.6 Treasury Liquidity Crunch from Concentrated yUSD Redemptions
Mitigations: Per-address yUSD holding caps, daily treasury redemption volume limits, mandatory 120% minimum treasury coverage ratio with automatic tax revenue acceleration triggers.
9.7 Malicious Governance Parameter Tampering Risk
Mitigations: All risk control thresholds, tax rates, vesting cycles and coverage ratios require WEI token governance votes with a 48-hour time lock before activation; all parameter changes are broadcast as permanent on-chain events, with emergency rule adjustments requiring a 66% supermajority vote.
10 Ecosystem Application Scenarios
Decentralized Exchange: Base trading pair quote currency, collateral and settlement medium;
Web3 Payments & Cross-Border Settlement: Merchant checkout, low-cost cross-chain value transfer;
Decentralized Lending & Yield Aggregation: Stablecoin collateral savings and yield-bearing vaults;
NFT & GameFi Economies: In-game asset pricing, marketplace settlement, liquidity mining collateral;
Multi-Chain Interoperability: Unified cross-chain stable asset to boost cross-network liquidity efficiency.
11 Project Development Roadmap
Phase 1: Core token contracts and base arbitrage stabilization logic mainnet deployment
Phase 2: Risk control contract launch – transaction caps, flash loan filters and Level 1 circuit breaker activation
Phase 3: Full oracle multi-source protection suite, Level 2 & 3 circuit breakers, whale position restriction system rollout
Phase 4: On-chain governance dashboard release with live risk control monitoring analytics
Phase 5: Compliance framework construction and institutional tooling integration
Phase 6: Full decentralized autonomous protocol operation with permissionless contract upgrade governance
12 Conclusion
The USDH protocol establishes a new generation of resilient algorithmic stablecoins built upon three core pillars: market-driven arbitrage stabilization, yUSD debt claim risk isolation, and sustainable treasury repayment infrastructure. By combining market self-correction, debt conversion to block death spirals, and a full suite of layered on-chain risk controls, USDH delivers a decentralized, anti-fragile and long-term sustainable stable asset primitive for Web3 global value transfer.
Disclaimer
This whitepaper v0.1 serves solely as a technical protocol design document and does not constitute investment advice of any form. Cryptographic digital assets carry extremely high market, technical and regulatory risks. All participants must conduct independent research and exercise extreme caution before interacting with the protocol.
README Quick Intro Version (Short for GitHub)
USDH: Market-Debt-Treasury Algorithmic Stablecoin v0.1
A decentralized algorithmic stablecoin protocol with 3 native tokens:
USDH: USD-pegged stablecoin (target band: 0.9 ~ 1.1 USD)
WEI: System native governance & equity token
yUSD: Discount debt token for deep de-pegging mitigation
Core Mechanism
Normal range (0.9 < USDH < 1.1): Two-way WEI-USDH arbitrage like UST/LUNA
Premium range (USDH > 1.1): Progressive mint tax to fill treasury and cool overvaluation
Discount range (USDH < 0.9): Burn USDH → split output into WEI + yUSD for the price gap, avoiding infinite WEI mint death spiral
Treasury
Treasury accumulates tax revenue, swap fees and yield profits to repurchase yUSD and pay interest for debt holders. Mandatory minimum 120% debt coverage ratio enforces solvency.
Full On-Chain Risk Control Suite
Prevent bank runs: Sliding window burn limits, daily global caps, cooldown attenuation
Flash loan defense: Prior-block asset validation, single-block volume limits, flash loan address blocklist
Whale manipulation control: Tiered holding quotas, reduced swap limits for large holders
Oracle protection: Multi-source median pricing, volatility filters, historical price fallback
Tiered circuit breakers (3 levels): Automatic swap restriction/halt during extreme de-pegging
Dual-layer transaction caps: Per-wallet sliding limits + global daily hard caps
Restricted yUSD redemption caps to avoid treasury liquidity exhaustion
All risk rules hard-coded in smart contracts, adjustable only via WEI governance with time lock delays. All operations are fully transparent and traceable on-chain.
