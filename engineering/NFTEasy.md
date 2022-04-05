[[October 5th, 2021]]

# Lesson 1
 - the tools we use (or choose to use) is often understated — any builder has strong opinions for these
 - Git and its history gives us a lot of insight about crypto
    - git commit trees are basically merkle trees — changing the code in one commit will change the hash and the ones after
    - in some way git is the first primitive blockchain
    - people say IPFS was awesome because of having the data being "content-addressable", but git has had that since 2005
    - blockchain isn't actually new technology
    - the whole point of this is to differentiate between "easy" — it means near to you (like within grasp) and "simple" which ultimately means "fewtwists" which is more related to "complex" which means "many twists" (lots of nuances)
 	   - so "easy" meaning its within reach
 - Node
    - the javascript runtime environment — takes JS out of the browser and into its own process (JS no longer lives in script tags)
 - Hardhat
    - previously it was really hard to develop for Ethereum — it basically only talks hexadecimal
    - truffle presented a framework where you can compile, run, test and debug your smart contracts
 	   - then it became very biased towards specific frontend frameworks
    - they needed to be highly opinionated in the beginning (truffle & embark), started moving away from
    - hardhat is somewhat of the standard framework-agnostic tool — no assumptions made for frontend and instead built a community around plugins.
    - if you're wondering about how to build communities, it's really about having this open architecture and we're really clear about how to add to it, to collectively contribute
    - Andy: in my opinion, community starts here (at the engineering, open-source level)
    - Q: where does the name hardhat come from? bitcoin → "hodl", ethereum has "buidl" and it seems to come from that meme factor (plus constructor workers wear hardhats to build safely and hardhat's intention is the same: "to give a safe environment to build on ethereum")
 - on Linux...
    - each OS made some very specific choices that empower and limit people that use them
    - they are nuanced and complex, but the link makes you think about the importance of these deep, low-level decisions

 - interesting links dropped in chat (primarily for understanding history & context)
    - [🔗](https://thebluebook.eth.link/)https://thebluebook.eth.link/
    - [🔗](https://hackernoon.com/how-to-generate-ethereum-addresses-technical-address-generation-explanation-25r3zqo)https://hackernoon.com/how-to-generate-ethereum-addresses-technical-address-generation-explanation-25r3zqo
    - [🔗](https://radicle.xyz/)https://radicle.xyz/
    - [🔗](https://eips.ethereum.org/EIPS/eip-721)https://eips.ethereum.org/EIPS/eip-721
    - [🔗](https://geek.sg/blog/my-journey-to-disclosing-a-vulnerability-that-can-lock-up-millions-in-ethereum)https://geek.sg/blog/my-journey-to-disclosing-a-vulnerability-that-can-lock-up-millions-in-ethereum
    - [🔗](https://blog.cloudflare.com/october-2021-facebook-outage/)https://blog.cloudflare.com/october-2021-facebook-outage/
    - [🔗](https://gov.gitcoin.co/t/the-gitcoin-gitcoindao-egregore-is-emerging/8200)https://gov.gitcoin.co/t/the-gitcoin-gitcoindao-egregore-is-emerging/8200
