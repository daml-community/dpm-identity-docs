# Verification Process
Currently the repository's security policy amounts to checking that the working tree satisfies gittuf policy. This check can be carried out by running the following commands, ensuring that [gittuf is installed](https://gittuf.dev/quickstart/):

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

