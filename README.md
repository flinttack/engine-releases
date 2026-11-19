# flinttack-engine releases

Prebuilt `flinttack-engine` executables for the [Flinttack](https://github.com/flinttack/flinttack)
CLI. The engine source is private; the binaries are built and attested here so that anyone
can verify where they came from.

Install the engine with the CLI:

```bash
flinttack engine install
```

Each release contains an archive per platform, `checksums.txt`, an SPDX SBOM and
`engine-manifest.json` (engine version, protocol version and archive checksums). Verify an
archive with:

```bash
gh attestation verify flinttack-engine_linux_amd64.tar.gz --repo flinttack/engine-releases
```

## Releasing

Pushing a `v*` tag in `flinttack/engine` triggers `release.yml` here through a
`repository_dispatch` event. It can also be run by hand with the tag as input.

Required secrets:

- `ENGINE_ACCESS_TOKEN` (this repository): read access to `flinttack/engine`.
- `ENGINE_RELEASES_DISPATCH_TOKEN` (`flinttack/engine`): permission to create dispatch
  events in this repository.
