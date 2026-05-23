# cg-runner

Custom GitHub Actions self-hosted runner image for [Common-ground](https://github.com/NickG123/Common-ground), built on top of `ghcr.io/actions/actions-runner` with the extra tools the Common-ground workflows assume are on PATH: `gh`, `jq`, `zip`, `unzip`.

## Image

Published as `ghcr.io/nickg123/cg-runner` (public). Multi-arch: `linux/amd64`, `linux/arm64`.

Tags:
- `latest` — head of `main`
- `sha-<short>` — every build
- `<branch>` — branch builds

## Use in ARC

In your `gha-runner-scale-set` Helm values:

```yaml
template:
  spec:
    containers:
      - name: runner
        image: ghcr.io/nickg123/cg-runner:latest
        command: ["/home/runner/run.sh"]
```

Pin a `sha-*` tag in production instead of `latest`.

## Build locally

```bash
docker build -t cg-runner:dev .
```
