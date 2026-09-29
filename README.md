# Strela releases

Signed release artifacts of self-hosted [Strela](https://github.com/surkovjs):
server (`strela-server`, `strela_admin`) and web client. The installer reads
the channel index `stable.json` from this branch and downloads the files of
each version from the GitHub Release `vX.Y.Z`.

Nothing here is trusted by location. The index and every release manifest are
signed with minisign; the installer accepts them only with its built-in key
and accepts an archive only with the size and SHA-256 of a verified manifest.

Release signing key:

```text
key id 88F0117610840274
RWR0AoQQdhHwiJfyBbabokF/qdBi9IizLIA8AYMcIgFQkj/gSAHmR5ZF
```

Manual check of a downloaded release:

```sh
minisign -Vm release-manifest.json -P RWR0AoQQdhHwiJfyBbabokF/qdBi9IizLIA8AYMcIgFQkj/gSAHmR5ZF
shasum -a 256 strela-server-*.tar.gz strela-web-*.tar.gz
```

The printed digests must equal the `sha256` values in the verified manifest.
