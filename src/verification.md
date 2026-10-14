# Verification Process
Currently the repository's security policy amounts to checking that the working tree satisfies gittuf policy. Ensure that [`gittuf` is installed](https://gittuf.dev/quickstart/)

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

