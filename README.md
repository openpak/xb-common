# Xbox Common Library

OpenPak's Xbox Common Library.

| | |
| --- | --- |
| Network | Original Xbox |
| Language | Go module `github.com/openpak/xb-common` |
| Used by | `xb-account`, `xb-auth`, `xb-gateway`, `xb-social`, `xb-enroll`, `xb-tou` |
| Licence | AGPL-3.0-only |

## Packages

| Package | Used by | Purpose |
|---|---|---|
| `xbcrypto` | account, auth (and krb, xbaccountapi) | RC4/HMAC, machine key derivation |
| `krb` | account, auth, gateway | Kerberos/DER structures, key derivation, ticket types |
| `xbaccountapi` | account, auth, gateway, social, enroll | xb-account client/server contract (`Resolver`, `DeviceKeys`, machine IDs) |
| `xbenrolapi` | account, enroll | enrolment HTTP contract |
| `xbfeature` | account, gateway, social, tou | gateway to feature gRPC stream (`openpak.xb.v1.Feature/Connect`) |
| `ratelimit` | account, enroll | keyed token-bucket limiter |

## Use

```sh
go env -w GOPRIVATE='github.com/openpak/*' GONOSUMDB='github.com/openpak/*'
go get github.com/openpak/xb-common@v0.1.0
```

```go
import "github.com/openpak/xb-common/xbcrypto"
```

Services pin a version in go.mod; details in [deploy](docs/deploy.md).

## Docs

- [Protocol](docs/protocol.md)
- [Evidence](docs/evidence.md)
- [Deploy](docs/deploy.md)
- [Notes](docs/notes.md)

## Licence

AGPL-3.0-only. See [LICENSE](LICENSE).
