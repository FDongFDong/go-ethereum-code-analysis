# go-ethereum code analysis


[go-ethereum](https://github.com/ethereum/go-ethereum)

PoS(Execution Client, Consensus Client, Validator Client)에 대해 조금 더 깊은 이해를 위해 첫번째로 Geth 코드를 분석 해보고자 합니다.

2023-05-19 기준으로 코드를 분석하겠습니다.

**사전 고지**

본 문서는  [Go-Ethereum analysis (English Version)](https://github.com/agiletechvn/go-ethereum-code-analysis) 문서를 재해석 및 제가 이해하기 쉽게 가공한 문서입니다.

## Table of contents

> 어느정도 정리가 되면 체크박스를 통해 알려 드리겠습니다.

-  [x] [go ethereum 디렉토리 분석](/go-ethereum-code-analysis.md)
- [ ] [rlp, rlpx 분석](/rlp-analysis.md)
- [trie source analysis](/trie-analysis.md)
- [ethdb analysis](/ethdb-analysis.md)
- [rpc analysis](/rpc-analysis.md)
- [p2p analysis](/p2p-analysis.md)
- [transaction](/transaction-analysis.md)
- [eth protocol analysis](/eth-analysis.md)
- **core analysis**
  - [blockchain index, chain_indexer analysis](/core-chain_indexer-analysis.md)
  - [bloom filter index, bloombits-analysis](/core-bloombits-analysis.md)
  - [ethereum trie, tree management, rollback, state-analysis](/core-state-analysis.md)
  - [transaction processing](/core-state-process-analysis.md)
  - **vm analysis**
    - [stack & data structure](/core-vm-stack-memory-analysis.md)
    - [instruction, jump table, interpreter analysis](/core-vm-jumptable-instruction.md)
    - [vm analysis](/core-vm-analysis.md)
  - **transaction pool management**
    - [transaction execution](/core-txlist-data-structure-analysis.md)
    - [transaction pool management](/core-txpool-analysis.md)
  - [genesis block](/core-genesis-analysis.md)
  - [blockchain-analysis](/core-blockchain-analysis.md)
- [miner analysis & CPU mining](/miner-analysis-CPU-mining.md)
- [pow, poa, pos algorithms](/pow-analysis.md)
- [ethereum test network Clique_PoA introduciton](/ethereum-Clique_PoA-introduction.md)
- [swarm, raw & file upload, pss and feed](/ethereum-swarm-introduction.md)
