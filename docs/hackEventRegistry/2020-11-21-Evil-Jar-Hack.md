# Evil Jar Hack
* **Project/Protocol:** Pickle Finance
* **Date & Time:** 
* * Exploit: Nov-21-2020 06-37-24 PM +UTC 
* * Fix (Estimated): Nov-22-2020 03-00-00 PM +UTC
* **Classification: Smart Contract Exploit**

## Summary
The "Evil Jar Hack" was a novel smart contract exploit of the Pickle Finance yield-generating  DeFi (Decentralized Finance) asset management platform which resulted in the draining of $19.76 Million of user funds (as DAI tokens). These funds were not recovered. 

## Context
The exploit centered around Pickle Finance's Pickle Jars (pJars), which are forked versions of Yearn Finance's yVaults (v1). The "Jars" hosted on the Pickle Finance platform each utilize different, community generated strategies for generating yield on user-deposited tokens. For example, taking advantage of opportunities for arbitrage between stablecoins on the Ethereum network or rewards programs operated by other DeFi platforms such as Uniswap and Curve for liquidity providers. Other attractive features of the Pickle Finance platform are the Pickle Jars' automation of processes like harvesting of LP rewards and providing participants the advantage of economies of scale that they would otherwise not enjoy as individuals implementing these yield farming strategies manually. Leading up to the hack over $150 million in value was locked in yield generating Pickle Jars and the platform was considered one of the hottest, community oriented DeFi projects of the time.

Hacker(s) targetted in this exploit Pickle Finance's cDai Jar, which had been launched just one day earlier. This cDai Jar utilized a strategy ([StrategyCmpdDaiV2](https://github.com/pickle-finance/contracts#pickle-jars-pjars)) that took advantage of [Compound Finance's](https://compound.finance/) COMP token rewards program to generate yield on user deposits of the DAI stablecoin. 

The Evil Jar Hack was notable for a number of reasons. 
* First, its technical complexity and the apparent Solidity and EVM experiste of the hacker. 
* Second, the magnitude of the funds drained. 
* Third, its timing - coming shortly after unrelated hacks of the [Harvest Finance](https://harvest.finance/) and [Akropolis](https://akropolis.io/) DeFi platforms. 
* Fourth, its highlighting of the difficulties distributed teams face in responding to real-time threat events.
* Fifth, its resulting in the first successful claim on a fully decentralized and KYC-free DeFi insurance platform - [COVER Protocol](https://coverprotocol.medium.com/11-21-20-claim-outcome-for-pickle-finance-aa2fcc56cb7c)
* Sixth, its resulting in the merger of Yearn Finance and Pickle Finance shortly after the resolution of the hack event.


Diagrams & Images
*[Pickle Jar 0 Strategy Diagram](https://picklefinance.medium.com/introducing-picklejars-70a311ab65c5)
![Pickle Jar 0 Strategy Diagram](https://miro.medium.com/max/1400/1*q-KP4QN2nFJxhSEtb_R88Q.png)
* [Pickle Evil Jar Attack Diagram](https://github.com/banteg/evil-jar)
![Pickle Evil Jar Attack Diagram](https://github.com/banteg/evil-jar/raw/master/assets/pickle-evil-jar.png)
* [Pickle Exploit Overview](https://www.rekt.news/pickle-finance-rekt/)
![Pickle Exploit Overview](https://www.rekt.news/content/images/size/w1600/2020/11/Pickle-Exploit-Overview.png)
* [Pickle Evil Jar Exploit Logic](https://twitter.com/orbxball/status/1330395696697143297?s=20)
![Pickle Evil Jar Exploit Logic](https://pbs.twimg.com/media/EnaDyfGXUAEfwon?format=png&name=900x900)

## Cause
Several vulnerabilities in the Pickle Finance smart contracts made this exploit possible. In fact the exploit relied on 8 separate vulnerabilities which needed to occur at the same time in order to allow the attacker to swap user funds from the legitimate Pickle Jar into "Evil" jars of their own. 

The 8 vulnerabilities (as reported by Jun-You Liu) were:
1. Lack of a sanity check on address argument
2. Allowance to pass _target & _data openly
3. Placement of withdrawForSwap in an unauthorized function
4. Placement of delegatecall in an unauthorized function
5. Whitelisted address has an arbitrary function
6. Whitelisted address is authorized to an unauthorized function
7. Public earn
8. Allowance to withdraw working asset from strategy

These vulnerabilities represent both previously existing flaws in the Pickle Jar Controller contract and new flaws that had been added in the latest version related to the enabling of direct swaps of funds by users between Jars. 

A full technical analysis of this attack has been prepared and [made public](https://github.com/banteg/evil-jar/blob/master/readme.md) by Yearn Finance core-dev "[Banteg](https://twitter.com/bantg)" who was among the team of developers who responded to the hack.

### Result
In addition to the loss of $19.76 Million in DAI tokens the price of Pickle Finance's native token (PICKLE) fell over 50% following news of the hack being widely reported in the DeFi community, first on Twitter and then in the press. 

In the immediate response to the hack Pickle users were urged to withdraw funds immediately from the platform, however a signficant amount of user tokens remained in vulnerable Jars requiring the efforts of a team of whitehat developers and hackers including [Julien Bouteloup](https://twitter.com/bneiluj), [Vasa Saini](https://twitter.com/vasa_develop), [Banteg](https://twitter.com/bantg), [Sam Sun](https://twitter.com/samczsun), [Emiliano Bonassi](https://twitter.com/emilianobonassi), and members of the Pickle Finance team.

This exploit also resulted in the first ever succesful insurance claim and payout utilizing the then-newly launched COVER Protocol smart-contract insurance platform. The claim was submitted on November 21st and passed a vote by the COVER Protocol community to pay out on November 23rd. This is notable also as the first succesful insurance claim on a decentralized and KYC-free DeFi insurance platform.

## Prevention
The Evil Jar hack event reveals the danger of forking existing smart contracts, even those that have been previously audited and apparently unnafected by hacks, and building new functionality on top of them. Future teams should take care to observe best practices and be aware of any publicly reported vulnerabilities in the contracts they are forking, such as the similar vulnerability within the Yearn Vault V1 smart contracts [disclosed](https://github.com/iearn-finance/yearn-security/blob/master/disclosures/2020-10-10.md) by Banteg and the Yearn team in October of 2020.

Additionally, the difficulty the Pickle team faced in its response to the hack event as a result of its decentralized governance structure (governance DAO) - specifically the use of timelocks and a team multisig - should be learned from. Disaster Response planning is a much needed practice in the DeFi industry.

## Helpful Links
* REKT Hack Response Post-Mortem: https://www.rekt.news/pickle-finance-rekt/
* Banteg Technical Post-Mortem: https://github.com/banteg/evil-jar
* Peckshield Exploit Analysis: https://peckshield.medium.com/pickle-incident-root-cause-analysis-5d73496ebc9f
* Jun-You Liu (@orbxball) Exploit Analysis: https://twitter.com/orbxball/status/1330395576593211392?s=20
* Vasa Saini (@vasa_develop) Event Overview: https://twitter.com/vasa_develop/status/1330532691205361664
* Transaction & Wallet Links
* * Hack TX: https://etherscan.io/tx/0xe72d4e7ba9b5af0cf2a8cfb1e30fd9f388df0ab3da79790be842bfbed11087b0
* * Full TX Trace: https://bloxy.info/tx/0xe72d4e7ba9b5af0cf2a8cfb1e30fd9f388df0ab3da79790be842bfbed11087b0
* *Full TX Trace: https://ethtx.info/mainnet/0xe72d4e7ba9b5af0cf2a8cfb1e30fd9f388df0ab3da79790be842bfbed11087b0
*  * Hack Contract: 0x2b0b02ce19c322b4dd55a3949b4fb6e9377f7913
*  * Hack Destination Wallet: https://etherscan.io/address/0x2b0b02ce19c322b4dd55a3949b4fb6e9377f7913
* Cover Protocol Medium Post Rergarding Insurance Claim Outcome: https://coverprotocol.medium.com/11-21-20-claim-outcome-for-pickle-finance-aa2fcc56cb7c
* TheBlock Article Regarding Pickle-Yearn Merger: https://www.theblockcrypto.com/post/85585/defi-merger-yearn-pickle-finance

## Project Details
* Project Summary: Pickle Finance is a decentralized protocol designed to use farming incentives, vaults, and governance to bring stablecoins closer to their pegs.  pVaults, short for Pickle Vaults, utilize different active strategies including leveraged flash loans to short off-peg stablecoins, to generate returns for pVault owners and the protocol. Pickle Protocol is governed by PICKLE token holders who are able to create and vote on proposals for changes to the protocol. (ht [DefiPulse](https://defipulse.com/pickle-finance))  
* Website: https://pickle.finance/
* Twitter: https://twitter.com/picklefinance
* Discord: https://discord.com/invite/uG6WhYkM8n
* Forum: https://forum.pickle.finance/
* Medium: https://picklefinance.medium.com/
* Telegram (English): https://t.me/picklefinance
* Telegram (Chinese) https://t.me/picklefinancechinese
* Governance: https://snapshot.page/#/pickle
* Documents: https://docs.pickle.finance/
* FAQs: https://pickle.fyi/
* Contracts: https://github.com/pickle-finance/contracts
* Pickle Jar Strategies: https://github.com/pickle-finance/contracts#pickle-jars-pjars
* DefiPulse: https://defipulse.com/pickle-finance
* Blockchain: Ethereum
* Launch Date: Sept-11-2020 
* Founders: Anonymous 
* Token Symbol: PICKLE
* Token Contract Address: 0x429881672B9AE42b8EbA0E26cD9C73711b891Ca5
* Forked: Yes. Yearn Finance (yVaults) & Sushiswap (Masterchef)
* Audited: Yes. [MixBytes](https://mixbytes.io/) & [Haechi](haechi.io)
* * MixBytes: Audit Report: https://github.com/pickle-finance/protocol/blob/master/audits/MixBytes_Audit_All_Strategies.pdf
* * Haechi Audit Summary: https://medium.com/haechi-audit/pickle-finance-smart-contract-audit-6aff9901eb25
* * Haechi Audit Report: https://github.com/pickle-finance/protocol/blob/master/audits/Haechi_Audit.pdf
* Pickle Jars Explained: https://picklefinance.medium.com/introducing-picklejars-70a311ab65c5


## Tags
TBD