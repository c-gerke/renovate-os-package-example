# renovate-os-package-example

Small fixture repo for testing Renovate updates against Ubuntu and Debian package versions.

The `renovate.json` file defines comment aliases such as `ubuntu-2404` and `debian-12`, then maps them to Renovate's built-in `deb` datasource with distro-specific registry URLs.

Active Dockerfile examples:

- `dockerfiles/Dockerfile.ubuntu-2404`
- `dockerfiles/Dockerfile.ubuntu-2604`
- `dockerfiles/Dockerfile.debian-12`
- `dockerfiles/Dockerfile.debian-13`
- `dockerfiles/Dockerfile.debian-14`

Each file contains pinned package versions like this:

```Dockerfile
# renovate: datasource=ubuntu-2404 depName=curl
ARG CURL_VERSION=8.5.0-2ubuntu10.6
```

When Renovate runs, it should read the comments, use the `deb` datasource, and propose a PR that updates stale `ARG` values.

Every Dockerfile tracks and installs these packages:

- `curl`
- `wget`
- `openssl`
- `git`
