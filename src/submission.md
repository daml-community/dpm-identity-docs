# Submission Process
Currently any changes to the repository need approval from 2 out of 3 of the following council members:

- Digital Asset
- Canton Foundation
- Obsidian Systems

This is dictated by the repo's gittuf policy.
The approval process takes place in GitHub via a PR. One positive review correponds to one approval vote.

The submission process is as follows:

1. A submitter (anyone) opens a GitHub PR, containing the changes to the repository.
2. The submitter requests a review from the three council members.
3. The council members each decide whether the changes are appropriate, and approves/denies the review.
4. Anyone merges the PR.

For an example PR, see [here](https://github.com/daml-community/dpm-identity/pull/24)

## Governance and M7
Note that in step (3), we haven't described an explicit set of rules to decide what "changes are appropriate" means. This explicit policy is a priority for later milestones (specifically Milestone 7), as currently the identites in the repository **will not change**. We are in the process of formalising a governance policy together with Digital Asset. The draft policy can be found [here](./M1GovernanceDraft.pdf). 

The current roadmap for M7 includes:

- A decision tree that governs whether to add keys to the repository. This should make explicit the valid forms of identification.
- A secure process for various key and audit removal processes:

    - Rotating keys
    - Removing a compromised key
    - Reporting a lost key
    - Removing a malicious actor from the repo
    - Removing a bad audit

  Outlining in each case what happens to audits in the repo
- A CLI tool that can be used to aid common processes
