Voting Dapp - Project Description
Overview:
The Voting Dapp is a decentralized application built on Ethereum using Solidity smart contracts. It allows users to participate in a transparent and tamper-proof voting process. Only the contract owner can add candidates and control the start and end of the voting session, while each participant is limited to a single, verifiable vote.

Key Features:

 Admin Control: Only the contract owner can add candidates and manage the voting session.

One Vote Per Wallet: Ensures fairness by preventing duplicate votes.

 Live Updates: Voting events (start, end, votes casted) are emitted for frontend apps to listen and update in real-time.

Secure & Transparent: Voting is stored immutably on the blockchain, open for anyone to verify.

 Dynamic Candidates: Admin can add any number of candidates before voting begins.

Smart Contract Functions:

addCandidate(string name) — Add new candidates (owner only).

startVoting() — Start the voting session.

vote(uint256 candidateId) — Cast a vote for a selected candidate.

endVoting() — End the voting session.

getCandidatesCount() — Get the number of candidates.

getCandidate(uint256 candidateId) — Retrieve details about a specific candidate.

Technologies Used:

Solidity (Smart Contract)

Ethereum Blockchain

Ethers.js / Web3.js (Frontend Integration)

Use Cases:

Club elections

DAO decision-making

Community polls

Simple blockchain-based elections

