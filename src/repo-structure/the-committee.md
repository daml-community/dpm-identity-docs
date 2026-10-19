# The Committee
Any notion of trust in the repository stems from the committee. No one else is given the ability to modify identities, which in turn decides who can add audits. The initial committee comprises two members:

- **Canton Foundation**
- **Obsidian Systems**

Each of which will be associated with a GPG key, representing the member's vote.
The committee members have a responsibility to keep the keys safe: they are the source of trust for the repo. We would advise generating a primary key on an air-gapped machine, then exporting a subkey to use.

## Gittuf Policy **(M1)**
These rules will be enforced by `gittuf` policy. The specific policy in effect for **M1** is:

- `obsidian-systems` and `canton-foundation` are both registered as **Policy Administrators** and in the **Root of Trust** (see [`gittuf` docs](https://gittuf.dev/documentation/maintainers/design#trust-levels) for a description of these roles). Among other things, this means that they can propose new policies, AND add new **Policy Administrators**.
- There is a threshold of 2 of 2 votes for every **Root of Trust** operation and **Policy Administrator** operation in the repository.

The current policies in effect are:

- Modification of any files not under the `audits/` folder requires 2 of 2 votes from the committee.
- Modification of files under the `audits/` folder can be done by anyone, provided that they have been registered in the repo. This has been done manually for now, but when **(M7)** is started, there will be an automated process for this.

To verify this policy for yourself, see the notes [here](../verification.md#listing-the-gittuf-policy).

## Adding to the committee **(M7)**
The proposal outlines a small initial committee, but as the repository expands in size, we will need to think about adding more members to the committee and additionally changing the threshold of votes required for certain operations. Adding a new committee member is a much more dangerous operation than just adding keys. We will need to have tighter checks to ensure a committee member is who they say they are AND can be trusted. This could mean verifying in-person. This will be properly formalised in the later milestones.
