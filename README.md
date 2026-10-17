# xb-common

Shared Go packages for the OpenPak original-Xbox services (`xb-account`,
`xb-auth`, `xb-gateway`, `xb-social`, `xb-enroll`, `xb-tou`). Module
`github.com/openpak/xb-common`. Only code imported by two or more services
lives here; it holds no feature state and no runtime.

| Package | Used by | Purpose |
|---|---|---|
| `xbcrypto` | account, auth (and krb, xbaccountapi) | RC4/HMAC, machine key derivation |
| `krb` | account, auth, gateway | Kerberos/DER structures, key derivation, ticket types |
| `xbaccountapi` | account, auth, gateway, social, enroll | xb-account client/server contract (`Resolver`, `DeviceKeys`, machine IDs) |
| `xbenrolapi` | account, enroll | enrolment HTTP contract |
| `xbfeature` | account, gateway, social, tou | gateway to feature gRPC stream (`openpak.xb.v1.Feature/Connect`) |
| `ratelimit` | account, enroll | keyed token-bucket limiter |

Single-service code stays in that service (`sgwire` in xb-gateway, `xbcodes` in xb-account).

## Using it (private module)

```sh
go env -w GOPRIVATE='github.com/openpak/*' GONOSUMDB='github.com/openpak/*'
go get github.com/openpak/xb-common@v0.1.0
```

Developers authenticate with `gh auth setup-git`. CI image builds read the module
with the job's `GITHUB_TOKEN` through a build secret (`.netrc`), see each
service's `release.yml`; the repo's Actions access setting is "accessible from
repositories in the organization". No tokens are stored in git.

## Development

```sh
GOWORK=off go build ./... && go vet ./... && go test -race ./...
```

Versioning: semver tags `vX.Y.Z`; services pin a version in go.mod and never use
`replace` directives in committed files.
