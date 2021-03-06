## [Link](https://ethos.dev/beacon-chain/)
## Notes
 - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fsecond-jeff%2FYC_Ld1fxi8.png?alt=media&token=c2df5775-8bd1-44d0-9937-30258615b9f4)
- First up, how scaling works in a typical system 
    - As a distributed system scales it has one of two choices: scale horizontally (more nodes) or vertically (more powerful nodes). In the spirit of decentralization, the choice here is for them to scale horizontally
    - The average person won't be able to acquire specialized hardware, so the result is centralization around either wealthier individuals or pooled resources.
    - **Sharding** is a form of horizontally partitioning a database (and thus modularize it to make it scalable)
- So for Ethereum, sharding looks like having a dynamic subset of nodes that process block by block
    - The main follow up here being: how do we still retain the security benefits of a large decentralized system while still lifting the requirement that every node needs to verify and execute every transaction? The implication being that with shards, an attacker could make a focused effort to attack a single shard (and act maliciously)
    - Ethereum's Solution: randomly shuffle the validators responsible for verifying/executing transaction on a given shard block. Every shard block gets assigned a randomly chosen "committee" of validators such that an attacker would need control over 1/3 of all of the validators to gain majority within a single shard (probabilistically)
- 
