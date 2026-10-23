# File Structure
The file structure we propose is:
```
identities/
    <id>/
        meta.json
        FA31...A3/
            key.asc
            evidence/
                ...
        B491...D5/
            key.asc
            revoke.json
            evidence/
                ...
audits/
    <package-id>/
        <identity>-<date>.json
        <identity>-<date>.json.sig
        <identity>-<date>.revoke.json
        <identity>-<date>.revoke.json.sig
```

Where:

- `identities/` contains directories corresponding to each identity in the repo
    - `<id>/` is a directory containing the history of all keys for an identity. The naming convention here is that `<id>` is the `kebab-case` version of the `Name` field of the gpg keys.
        - `meta.json`: Metadata about the identity
        - `<key>/`: Directory containing information about a particular key
            - `key.asc`: The exported GPG public key. Generated via `gpg --export --armor`
            - `revoke.json`: A JSON file indicating that the key has been revoked and why.
            - `evidence/`: Directory containing evidence used by the committee when evaluating the key's identity
- `audits/` contains subfolders corresponding to package ids:
    - `<package-id>/` contains all audits of a package id
        - `<identity>-<date>.json` is an audit of `<package-id>` by `<id-fp>` on `<date>`. Note: No claims are made by this filename, it's solely to reduce collisions. All of the significant content is contained within the file. It conforms to the specification outlined in `schemas/audit-report.json5`.
        - `<identity>-<date>.json.sig` is the detached signature of the audit.
        - `<identity>-<date>.revoke.json` expresses a revocation of the audit.
        - `<identity>-<date>.revoke.json.sig` is the detached signature of the revocation.

We decide that a key for an identity is valid by checking that it hasn't been revoked.

