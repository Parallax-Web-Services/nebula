# NEBULA

NEBULA connects paired NUCLEUS machines across networks and provides an operator CLI for organizations and clusters. This repository contains the CLI entry point, cPanel integration, and infrastructure tooling. NUCLEUS supplies the fabric identity, membership, transport, and shared command implementation. The Go module pins its runtime dependency in [go.mod](go.mod).

## Build the CLI

Use Go 1.23 or later on Linux or WSL with Git read access to both repositories. Configure Git credentials for GitHub before fetching private dependencies. If you use GitHub SSH keys, configure Git to use SSH for the Parallax organization.

```sh
git config --global url."git@github.com:Parallax-Web-Services/".insteadOf https://github.com/Parallax-Web-Services/
export GOPRIVATE="github.com/Parallax-Web-Services/*${GOPRIVATE:+,$GOPRIVATE}"
go build -o bin/nebula ./cmd/nebula
./bin/nebula version
```

The CLI reuses the local NUCLEUS identity by default. For an isolated installation, set `NEBULA_HOME` to an absolute path. [CLI commands](docs/NEBULA_CLI.md) · [WAN transport](docs/NEBULA.md)

## Source locations

- The shared Go runtime and original branch history live in [NUCLEUS](https://github.com/Parallax-Web-Services/nucleus). The NEBULA tooling history was extracted through [the original tooling commit](https://github.com/Parallax-Web-Services/nucleus/commit/925015c17a817dd4ac83fc21ca79aa2cbcc2d18b).
- The hosted NEBULA dashboard is maintained in the marketing repository. [Dashboard source](https://gitlab.com/parallax-web-services/marketing/-/tree/master/apps/nebula-dashboard)
- The standalone panel and optional cPanel/WHM integration are described in the [platform contract](docs/NEBULA_PLATFORM.md) and [plugin documentation](apps/nebula-cpanel/README.md).

## License

Parallax Web Services, Inc. licenses NEBULA under the [MIT License](LICENSE). Third-party components retain their own terms, including [coder/websocket (ISC)](THIRD_PARTY_NOTICES/coder-websocket-LICENSE).
