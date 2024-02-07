This is my own method for concluding if a proposa can be accepted or rejected:

```
function calculateCurrentState() private view returns (bool) {
    Proposal storage proposal = proposal_history[counter];

    uint256 totalVotes = proposal.approve + proposal.reject + proposal.pass;

    // Calculate the ratio of approve votes to total votes
    uint256 approveRatio = proposal.approve * 100 / totalVotes;

    // Calculate the ratio of reject votes to total votes
    uint256 rejectRatio = proposal.reject * 100 / totalVotes;

    // If the approve ratio is greater than or equal to 60%, the proposal passes
    if (approveRatio >= 60) {
        return true;
    }

    // If the reject ratio is greater than or equal to 40%, the proposal fails
    if (rejectRatio >= 40) {
        return false;
    }

    // Otherwise, the proposal is still active
    return false;
}
```
