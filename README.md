# Cypherrum Releases

Public distribution of Cypherrum — desktop vault encryption with
post-quantum mesh sharing.

- **Website**: <https://cypherrum.com>
- **Downloads**: [Latest release](https://github.com/logiqum/cypherrum-releases/releases/latest) · [All releases](https://github.com/logiqum/cypherrum-releases/releases)
- **Release notes**: [RELEASE-NOTES.md](./RELEASE-NOTES.md) · [Full changelog](https://cypherrum.com/changelog)
- **User guide**: <https://cypherrum.com/docs/user-guide>
- **Discussions / support**: [GitHub Discussions](https://github.com/logiqum/cypherrum-releases/discussions)
- **Security disclosure**: see [SECURITY.md](./.github/SECURITY.md)

## Verify a download

Each release ships `SHA256SUMS-<version>` alongside the binaries.
Recent releases also include `SHA256SUMS` + `SHA256SUMS.sig`
(ed25519-signed manifest used by Cypherrum's auto-update).

```bash
sha256sum -c SHA256SUMS-<version>
```

## Mesh and the optional relay

Cypherrum's mesh sharing works LAN-only out of the box — devices on the
same network discover each other and sync directly.

For cross-network sync (different LANs, mobile networks, traveling between
sites), Cypherrum can route through a **public relay**. Logiqum operates
one at `relay.cypherrum.com`; it is enabled by default and is the path
used by invite links and asynchronous shares.

The relay only ever sees end-to-end-encrypted payloads — vault contents,
share envelopes, and inbox messages are all encrypted client-side before
they leave a device. The relay cannot read them.

## License

Proprietary. See [cypherrum.com](https://cypherrum.com) for licensing and terms.
