# infra/

Infrastructure as code for Build Better OS.

## Purpose

All infrastructure that the platform runs on — compute, storage, networking, DNS, secrets management, and CI/CD configuration — is defined here as code. Infrastructure is version-controlled, reviewed, and deployed the same way as application code.

## Folder Structure

```
infra/
└── README.md     ← this file
```

Infrastructure definitions will be added as the technology stack is decided and the first services are deployed.

**Expected future structure:**
```
infra/
├── environments/     ← per-environment configuration (staging, production)
├── modules/          ← reusable infrastructure modules
├── networking/       ← VPC, DNS, load balancers
├── deployments/      ← per-service and per-app deployment definitions
└── observability/    ← logging, metrics, tracing infrastructure
```

Note: the subdirectory is named `deployments/`, not `services/`, to avoid confusion with the top-level `services/` directory which holds service code.

## What Belongs Here

- Compute definitions (containers, serverless functions, VMs)
- Storage provisioning (databases, object storage, queues)
- Networking configuration (VPC, subnets, DNS, TLS)
- Secrets and environment configuration management
- CI/CD pipeline infrastructure (if not managed via GitHub Actions)
- Observability stack: log aggregation, metrics, tracing

## What Does NOT Belong Here

- Application code (that belongs in `apps/`, `services/`, or `platform/`)
- GitHub Actions workflow definitions (those belong in `.github/workflows/`)
- Application-level configuration that is not infrastructure (keep that in each service)

## Tooling

Infrastructure tooling has not yet been selected. Candidates will be evaluated and the decision recorded as an ADR in `docs/adr/`.

## Relationships

- Infra **provisions the environment** that services and apps run in
- Infra is **referenced by** `.github/workflows/` for deployment steps
- Infra definitions map to **services** in `services/` and `apps/`

## Environments

| Environment | Purpose |
|---|---|
| `local` | Developer machine (not defined here — see `docs/guides/`) |
| `staging` | Pre-production validation |
| `production` | Live system |

## Future Extensions

- Disaster recovery and backup configuration
- Cost allocation and resource tagging standards
- Environment promotion workflow (staging → production)
