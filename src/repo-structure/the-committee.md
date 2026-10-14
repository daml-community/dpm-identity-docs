# The Committee
Any notion of trust in the repository stems from the committee. No one else is given the ability to modify identities, which in turn decides who can add audits. The initial committee is comprised of three members:

- **Digital Asset**
- **Canton Foundation**
- **Obsidian Systems**

Each of which will be associated with a GPG key, representing the member's vote.
The committee members have a responsiblity to keep the keys safe: they are the source of trust for the repo. We would advise generating a primary key on an airgapped machine, then exporting a subkey to use.

## Adding to the committee **(M7)**
The proposal outlines an initial committee of 3 members, but as the repository expands in size, we will need to think about adding more members to the committee and additionally changing the threshold of votes required for certain operations. Adding a new committee member is a much more dangerous operation than just adding keys. We will need to have tighter checks to ensure a committee member is who they say they are AND can be trusted. This could mean verifying in-person. This will be properly formalized in the later milestones.
