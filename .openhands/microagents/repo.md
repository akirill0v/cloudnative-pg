# CloudNativePG

CloudNativePG is a Kubernetes operator for managing PostgreSQL databases throughout their entire operational lifecycle—from deployment to ongoing maintenance. It's a CNCF project originally built by EDB that enables running highly available PostgreSQL clusters natively in Kubernetes, leveraging the operator pattern and eventual consistency principles.

## File Structure

- **api/v1/** - Kubernetes API type definitions for CRDs (Cluster, Backup, Pooler, etc.)
- **cmd/** - Entry points for the operator (`manager`) and kubectl plugin (`kubectl-cnpg`)
- **config/** - Kubernetes manifests (CRDs, RBAC, webhooks, Helm charts, OLM configs)
- **internal/** - Core operator logic including controllers, webhooks, and instance management
- **pkg/** - Reusable packages (certs, postgres utilities, specs, reconciler helpers)
- **tests/** - E2E test suites using Ginkgo
- **docs/** - Documentation source (MkDocs-based)
- **hack/** - Development and release scripts
- **contribute/** - Contributor guides and development environment setup

## Development Commands

```bash
make build          # Build manager and kubectl-cnpg binaries
make test           # Run unit tests with coverage
make lint           # Run golangci-lint
make manifests      # Generate CRDs and RBAC manifests
make generate       # Generate Go code (deepcopy, etc.)
make docker-build   # Build container image
make deploy         # Deploy operator to current kubectl context
make e2e-test-kind  # Run E2E tests using kind cluster
```

## Getting Started

1. Install Go (check `go.mod` for version) and Docker
2. Run `make build` to compile binaries
3. Use `make kind-cluster` to create a local test cluster
4. Run `make deploy-locally` to build and deploy the operator locally
5. Follow [conventional commits](https://www.conventionalcommits.org/) and sign commits with DCO (`git commit -s`)

See `contribute/development_environment/README.md` for detailed setup instructions.
