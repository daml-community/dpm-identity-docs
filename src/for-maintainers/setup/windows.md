# Windows Setup
Install `gpg4win` from winget by running the following from powershell:

```sh
winget install GnuPG.Gpg4win
```

## Configuring `gpg`
We must first generate a `gpg` key, if you do not already have one, to represent your organisation. It is important that YOU DO NOT LOSE THIS KEY. We would advise that this key is kept somewhere secure by the organisation. Once this key is generated, the most secure practice is then to distribute a subkey to anyone that wishes to use this key, and to never use the key directly. The following documents the process of:
1. Generating an organisation `gpg` key and creating a subkey
2. Exporting the subkey public key
3. Exporting your github id

### Generating an organisation `gpg` key and creating a subkey
To generate a `gpg` key and add a subkey, run:
```sh
gpg --quick-generate-key "Org Name" rsa3072 default never
gpg --quick-add-key '<pub-key-fingerprint>' rsa3072 sign 1y
```

### Exporting the subkey
To export the subkey run:
```sh
gpg --list-secret-keys --with-subkey-fingerprint
gpg --export --armor "<SUBKEYFINGERPRINTNOSPACES>"
```

### Exporting your github id
To get your github `id`, run:
```sh
curl -s https://api.github.com/users/<username> | jq '.id'
```

<!-- The altering of the policy is done in two stages: -->
<!-- 1. An existing maintainer proposes an amendent to the policy -->
<!-- 2. Another maintainer co-signs this amendment -->
<!---->
<!-- ### Proposing an amendment (Current Maintainer 1) -->
<!-- A current **maintainer** must: -->
<!-- - Add the identity of the new organisation as a **policy signer**: -->
<!--   ```sh -->
<!--   gittuf policy add-person -k "gpg:<current-member-gpg-key>" --public-key "gpg:<new-member-gpg-key>" --person-ID "<new-member-name>" --associated-identity "https://gittuf.dev/github-app::<new-member-github-username>+<new-member-github-id>" -->
<!--     ``` -->
<!-- - propose an amendment to the security policy so as to allow the new member to vote: -->
<!--   ```sh -->
<!--   gittuf policy remove-rule --rule-name all-files -->
<!--   gittuf policy add-rule \ -->
<!--     --signing-key "gpg:<current-member-gpg-key>" \ -->
<!--     --rule-name "all-files" \ -->
<!--     --rule-pattern "file:*" \ --authorize "<current-member-1-name>" \ -->
<!--     --authorize "<current-member-2-name>" \ -->
<!--     -- ... \ -->
<!--     --authorize "<new-member-name>" \ -->
<!--     --threshold 2 -->
<!--     ``` -->
<!---->
<!-- ### Approving the ammendement (Current Maintainer 2) -->
<!-- Another **maintainer** must then counter-sign this policy on their own checked-out repo: -->
<!-- ```sh -->
<!-- gittuf policy remote pull -->
<!-- gittuf policy sign -k "gpg:<member-2-key>" -->
<!-- gittuf policy stage -->
<!-- gittuf policy apply --create-rsl-entry -->
<!-- ``` -->
<!---->
