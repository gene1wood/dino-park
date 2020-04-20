# DinoPark - An Introduction

This document is work in progress but should give some high level overview
and point to the right places.

## Repositories

### Front-End

https://github.com/mozilla-iam/dino-park-front-end

### Back-End

Rust:
- https://github.com/mozilla-iam/dino-park-fence \
  Profile API and proxy to search and orgchart
- https://github.com/mozilla-iam/dino-park-fossil \
  Picture API
- https://github.com/mozilla-iam/dino-park-lookout \
  Handles web hooks for profile updates
- https://github.com/mozilla-iam/dino-park-whoami \
  Verified Identities API
- https://github.com/mozilla-iam/dino-park-packs \
  Access Groups Management API

NodeJS:
- https://github.com/mozilla-iam/dino-park-search \
  Search API
- https://github.com/mozilla-iam/dino-park-tree \
  Org-chart API

### Libraries

Rust:
- https://github.com/mozilla-iam/cis_profile-rust \
  Rust representation of [profile v2] and crypto helpers for signing
- https://github.com/mozilla-iam/cis_client-rust \
  A client implementation for [Person API] and Change API
- https://github.com/mozilla-iam/dino-park-trust \
  Trust levels (user trust, groups trust, and AAL)
- https://github.com/mozilla-iam/dino-park-gate \
  Middleware for [actix] supporting trust levels and claim checks
- https://github.com/mozilla-iam/dino-park-guard \
  [proc macro] for easy route annotations to guard with trust levels
- https://github.com/mozilla-iam/dino-park-oidc \
  Basic [OIDC] helper

## Infrastructure and 3rd Party Services

- DinoPark micro services run in [Kubernetes]
- Pictures are stored in [S3]
- Profile search is backed by [Elasticsearch]
- Group management is build on top of [PostgreSQL] using [Diesel]

## General Micro Service Repository Structure

All DinoPark micro service repositories share a common structure.

### Kubernetes (k8s)

All kubernetes related configuration files are located in the `k8s` directory.
They provide a basic helm chart for the service and potential dependencies.

```ini
k8s
├── Chart.yaml
├── templates
│   ├── 00-namespace.yaml
│   ├── deployment.yaml
│   └── service.yaml
├── values # environment specific overwrites / variables
│   ├── dev.yaml
│   ├── prod.yaml
│   └── test.yaml
└── values.yaml # common variables
```

To render the chart for `dev` use:
```
helm template -f k8s/values.yaml -f k8s/values/dev.yaml k8s/
```

### Docker

The docker image produced by a repository is controlled via the `Dockerfile` or
`Dockerfile.local`. The same image is only build once and used in all environments.

### Terraform

Infrastructure is managed via terraform. All related files are located in the `terraform`
directory of the repository.

```ini
terraform
├── codebuild # codebuild and permissions for releasing
├── dev
├── prod
└── test
```

### Building

DinoPark services are built and deployed via [AWS Codebuild]. See `buildspec.yaml`.

### Deploying

Every push to master will result in a build and deployment to the dev environment.
Releasing to test and prod can be done via tags. Any tag with a `-test` suffix will be
deployed to the test environment. Any tag with a `-prod` suffix will be deployed to
production.

**Note: only tag a commit that actually triggered a build**

[profile v2]: https://github.com/mozilla-iam/cis/blob/master/docs/Profiles.md
[Person API]: https://github.com/mozilla-iam/cis/blob/master/docs/PersonAPI.md
[actix]: https://actix.rs/
[proc macro]: https://doc.rust-lang.org/reference/procedural-macros.html
[OIDC]: https://openid.net/connect/
[Kubernetes]: https://kubernetes.io/
[S3]: https://aws.amazon.com/s3/
[Elasticsearch]: https://www.elastic.co/elasticsearch/
[PostgreSQL]: https://www.postgresql.org/
[Diesel]: https://diesel.rs/

[AWS Codebuild]: https://aws.amazon.com/codebuild/