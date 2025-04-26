// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract VotingDapp {
    struct Candidate {
        string name;
        uint256 voteCount;
    }

    address public owner;
    bool public votingActive;
    Candidate[] public candidates;
    mapping(address => bool) public hasVoted;

    // Events
    event VoteCasted(address indexed voter, uint256 indexed candidateId);
    event VotingStarted();
    event VotingEnded();

    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can perform this action");
        _;
    }

    modifier votingOngoing() {
        require(votingActive, "Voting is not active");
        _;
    }

    constructor() {
        owner = msg.sender;
    }

    // Owner can add candidates before voting starts
    function addCandidate(string memory _name) external onlyOwner {
        require(!votingActive, "Cannot add candidates after voting started");
        candidates.push(Candidate({ name: _name, voteCount: 0 }));
    }

    // Start the voting
    function startVoting() external onlyOwner {
        require(!votingActive, "Voting already active");
        require(candidates.length > 0, "Add at least one candidate");
        votingActive = true;
        emit VotingStarted();
    }

    // End the voting
    function endVoting() external onlyOwner votingOngoing {
        votingActive = false;
        emit VotingEnded();
    }

    // Vote for a candidate
    function vote(uint256 _candidateId) external votingOngoing {
        require(!hasVoted[msg.sender], "You have already voted");
        require(_candidateId < candidates.length, "Invalid candidate ID");

        candidates[_candidateId].voteCount += 1;
        hasVoted[msg.sender] = true;

        emit VoteCasted(msg.sender, _candidateId);
    }

    // Get the number of candidates
    function getCandidatesCount() external view returns (uint256) {
        return candidates.length;
    }

    // Get a candidate details by ID
    function getCandidate(uint256 _candidateId) external view returns (string memory name, uint256 voteCount) {
        require(_candidateId < candidates.length, "Invalid candidate ID");
        Candidate storage candidate = candidates[_candidateId];
        return (candidate.name, candidate.voteCount);
    }
}
