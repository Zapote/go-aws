# go-aws

Docker images combining Go, AWS CLI, and kubectl on Alpine Linux. Designed for CI/CD pipelines that need to build Go applications and deploy to AWS/Kubernetes.

## What's included

- **Go** (Alpine-based official image)
- **AWS CLI** (`aws-cli` from Alpine packages)
- **kubectl** (latest stable, with SHA256 verification)
- **Docker CLI** (for Docker-in-Docker workflows)
- **govulncheck** (Go vulnerability scanner)
- **Utilities:** `curl`, `jq`, `gettext`, `unzip`, `git`, `bash`

## Available tags

| Tag | Go version |
|-----|------------|
| `1.25.7-alpine` | 1.25.7 |
| `1.25.6-alpine` | 1.25.6 |
| `1.25.5-alpine` | 1.25.5 |
| `1.25.3-alpine` | 1.25.3 |
| `1.25-alpine` | 1.25 |
| `1.24.1-alpine` | 1.24.1 |
| `1.23-alpine` | 1.23 |
| `1.22.0-alpine` | 1.22.0 |
| `1.21.3-alpine` | 1.21.3 |
| `1.20-alpine` | 1.20 |
| `1.19.1-alpine` | 1.19.1 |
| `1.18-alpine` | 1.18 |

## Usage

```bash
docker pull zapote/go-aws:1.25.7-alpine
```

```bash
docker run --rm zapote/go-aws:1.25.7-alpine go version
```

### In a CI pipeline (GitHub Actions example)

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container:
      image: zapote/go-aws:1.25.7-alpine
    steps:
      - uses: actions/checkout@v4
      - run: go build ./...
      - run: aws s3 cp binary s3://my-bucket/
      - run: kubectl apply -f deploy.yaml
```
