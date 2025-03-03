# Original Wiki
[List of Security Vulnerabilities](https://github.com/runtimeverification/verified-smart-contracts/wiki/List-of-Security-Vulnerabilities#integer-arithmetic)


# Formally Verified Smart Contracts

This repository contains smart contracts that have been formally verified by
[Runtime Verification](http://runtimeverification.com) and/or collaborators.

To verify a smart contract, we need to first produce a formal specification
stating *what* the smart contract is supposed to do.
This is often the most difficult part of the verification effort, requiring
sometimes several rounds of discussions and meetings with the owners of the
smart contract, to ensure that everybody is on the same page regarding the
intended functionality of the smart contract.
Not surprisingly, many bugs or opportunities for improvement in the smart
contract code are found at this early stage.
Then we need to show that the binary or low-level code
(e.g., [EVM binary][KEVM] or [IELE code][IELE]) generated
by the compiler from the smart contract high level code
(e.g., [Solidity] or [Vyper]) indeed satisfies the specification.
In our approach the proofs use [reachability logic],
a generalization of Hoare logic, separation logic and modal logic, and are
performed using the [K-framework].
The K framework takes a formal semantics of a language as trusted input
(e.g., that of [EVM][KEVM] or [IELE]), and then uses
it to symbolically execute the smart contract exhaustively on all paths,
making use of SMT solvers like [Z3] to solve the mathematical domain constraints.

<!--
* **2018-??-??** Casper - Ethereum Foundation
* **2018-??-??** Fabian Vogelsteller's ICO contract and ICO schema
-->

## List of Verified Smart Contracts

* **2020-01-21** [Ethereum 2.0 Deposit contract](/deposit/README.md)
* **2019-02-27** [GnosisSafe contract](/gnosis/GnosisSafe_RuntimeVerification.pdf)
* **2018-10-12** [Uniswap contract](/uniswap/README.md)
* **2018-07-12** [Ethereum Casper FFG contract](/casper/README.md)
* **2018-03-12** [DappSys DSToken ERC20 token contract](/erc20/ds-token/README.md)
* **2018-02-28** [Bihu KEY token operation contracts](/bihu/README.md)
* **2018-01-30** [MyKidsEducationToken ERC20 token contract](/erc20/hobby/README.md)
* **2018-01-26** [OpenZeppelin ERC20 token contract](/erc20/zeppelin/README.md)
* **2018-01-16** [HackerGold (HKG) ERC20 token contract](/erc20/hkg/README.md)
* **2017-12-23** [Philip Daian's Vyper ERC20 token contract](/erc20/vyper/README.md)

## Resources

We use the [K-framework] and its verification infrastructure throughout the formal verification effort.
All of the formal specifications are mechanized within the K-framework as well.
Therefore, some background knowledge about the K-framework would be necessary for reading and fully understanding the formal specifications and reproducing the mechanized proofs.
We refer the reader to the following resources for background knowledge about the K-framework and its verification infrastructure.

* [K-framework]
  * [Download] and [install]
  * [K tutorial]
  * [K editor support]
* [KEVM]: an executable formal semantics of the EVM in K
  * [Jellopaper]: reader-friendly formatting of KEVM
  * [KEVM research paper]
* [K reachability logic prover]
  * [eDSL]: domain-specific language for EVM-level specifications
* [ERC20-K]: a formal specification of the high-level business logic of [ERC20]
* [ERC20-EVM]: an EVM-level refinement of ERC20-K
* [ERC777-K]: a formal specification of the high-level business logic of [ERC777]

## License

Copyrightable work in this repository is licensed by Runtime Verification, Inc. under the terms of [The Reproducibility License 1.1.0](/LICENSE.md), a restrictive license.  That license is very readable, and you should read it.  Most will want to pay special attention to its [Reproducibility section](./LICENSE.md#reproducibility).

Other parts of the proof toolchain, including the K-framework, are licensed under different, open source terms, like those of The University of Illinois/NCSA Open Source License.

## Disclaimer

This repository does not constitute legal or investment advice. The preparers of this repository present it as an informational exercise documenting the due diligence involved in the secure development of the target contract only, and make no material claims or guarantees concerning the contract's operation post-deployment. The preparers of this repository assume no liability for any and all potential consequences of the deployment or use of this contract.

*The formal verification results presented here only show that the target contract behaviors meet the formal (functional) specifications. Moreover, the correctness of the generated formal proofs assumes the correctness of the specifications and their refinement, the correctness of [KEVM], the correctness of the [K-framework]'s [reachability logic theorem prover], and the correctness of the [Z3] SMT solver. The presented result makes no guarantee about properties not specified in the formal specification. Importantly, the presented formal specification considers only the behaviors within the EVM, without considering the block/transaction level properties or off-chain behaviors, meaning that the verification result does not completely rule out the possibility of the contract being vulnerable to existing and/or unknown attacks.*

Smart contracts are still a nascent software arena, and their deployment and public offering carries substantial risk. This repository makes no claims that its analysis is fully comprehensive, and recommends always seeking multiple opinions and audits.

This repository is also not comprehensive in scope, excluding a number of components critical to the correct operation of this system.

The possibility of human error in the manual review process is very real, and we recommend seeking multiple independent opinions on any claims which impact a large quantity of funds.


[KEVM]: <https://github.com/kframework/evm-semantics>
[K-framework]: <http://www.kframework.org>
[reachability logic theorem prover]: <http://fsl.cs.illinois.edu/index.php/Semantics-Based_Program_Verifiers_for_All_Languages>
[K reachability logic prover]: <http://fsl.cs.illinois.edu/index.php/Semantics-Based_Program_Verifiers_for_All_Languages>
[Download]: <https://github.com/kframework/k5/releases>
[install]: <https://github.com/kframework/k5/blob/master/README.md>
[K tutorial]: <https://github.com/kframework/k5/tree/master/k-distribution/tutorial>
[K editor support]: <https://github.com/kframework/k-editor-support>
[Jellopaper]: <https://jellopaper.org/>
[KEVM technical report]: <https://www.ideals.illinois.edu/handle/2142/97207>
[KEVM research paper]: <http://fsl.cs.illinois.edu/FSL/papers/2018/hildenbrandt-saxena-zhu-rodrigues-daian-guth-moore-zhang-park-rosu-2018-csf/hildenbrandt-saxena-zhu-rodrigues-daian-guth-moore-zhang-park-rosu-2018-csf-public.pdf>
[Z3]: <https://github.com/Z3Prover/z3>
[eDSL]: </resources/edsl.md>
[ERC20]: <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md>
[ERC20-K]: <https://github.com/runtimeverification/erc20-semantics>
[ERC20-EVM]: </resources/erc20-evm.md>
[ERC777]: <https://github.com/ethereum/eips/issues/777>

[IELE]: <https://github.com/runtimeverification/iele-semantics>
[Solidity]: <https://solidity.readthedocs.io/en/develop/>
[Vyper]: <https://github.com/ethereum/vyper>
[reachability logic]: <http://fsl.cs.illinois.edu/index.php/Reachability_Logic>
[ERC777-K]: <https://github.com/runtimeverification/erc777-semantics>
