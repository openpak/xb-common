# Deploy: xb-common

## Using it (private module)

```sh
go env -w GOPRIVATE='github.com/openpak/*' GONOSUMDB='github.com/openpak/*'
go get github.com/openpak/xb-common@v0.1.0
```

Developers authenticate with `gh auth setup-git`. CI image builds read the module with the job's `GITHUB_TOKEN` through a build secret (`.netrc`), see each service's `release.yml`; the repo's Actions access setting is "accessible from repositories in the organization". No tokens are stored in git.

## Development

```sh
GOWORK=off go build ./... && go vet ./... && go test -race ./...
```

Versioning: semver tags `vX.Y.Z`; services pin a version in go.mod and never use `replace` directives in committed files.
