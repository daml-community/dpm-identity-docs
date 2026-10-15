# Verification Process
Currently the repository's security policy amounts to checking that the working tree satisfies gittuf policy. Ensure that [`gittuf` is installed](https://gittuf.dev/quickstart/), that gpg signing for commits [has been enabled](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key), and that the repository has been cloned via:

```sh
gittuf clone git@github.com:daml-community/dpm-identity
```

*NOTE:* cloning via `gittuf` is important, as it pulls the correct git refs.

## Listing the `gittuf` policy
The gittuf policy can be listed via running:

*To list all principals*
```sh
gittuf policy list-principals
```

*To list all rules*
```sh
gittuf policy list-rules
```

## Verifying the `gittuf` policy
Helper commands are provided to check that the repo satisfies `gittuf` policy. Run the following:

**Linux/macOS**

From bash:
```sh
sh ./ci/verify.sh
```

**Windows**

From powershell:
```ps1
.\ci\verify.ps1
```

### A practical demo
The following demonstrates a user violating this policy by creating the files:

  - `identities/my-id/meta.json`
  - `identities/my-id/my-fp/key.asc`

Without the changes being approved by two council members.

```sh
git checkout master
mkdir -p identities/my-id/my-fp/
touch identities/my-id/meta.json
touch identities/my-id/my-fp/key.asc
git add .
git commit -m “Add my-id without council approval”
gittuf rsl record master --local-only
sh ci/verify.sh
```

