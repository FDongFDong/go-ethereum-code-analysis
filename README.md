# go-ethereum code analysis

[go-ethereum](https://github.com/ethereum/go-ethereum)

PoS(Execution Client, Consensus Client, Validator Client)에 대해 조금 더 깊은 이해를 위해 첫번째로 Geth 코드를 분석 해보고자 합니다.

**사전 고지**

본 문서는  [Go-Ethereum analysis (English Version)](https://github.com/agiletechvn/go-ethereum-code-analysis), [Go-Ethereum analysis (한국어)](https://github.com/scalalang2/go-ethereum-code-analysis) 문서를 재해석 및 제가 이해하기 쉽게 가공한 문서입니다.

## Table of contents

- [go ethereum code analysis (account, smart contract, logs, etc...)](/go-ethereum-code-analysis.md)
- [yellow book symbol index](symbol-index.md)
- [rlp, rlpx analysis](/rlp-analysis.md)
- [trie source analysis](/trie-analysis.md)
- [ethdb analysis](/ethdb-analysis.md)
- [rpc analysis](/rpc-analysis.md)
- [p2p analysis](/p2p-analysis.md)
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
