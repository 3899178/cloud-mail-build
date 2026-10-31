# Cloud Mail Linux build coordination

This public repository coordinates image acceptance and publication for https://github.com/3899178/cloud-mail. Application development remains in that repository.

- `linux-acceptance.yml` is the initial acceptance-only workflow. It reads its pinned application commit, has read-only permissions and does not publish or deploy.
- `publish-mail-sync.yml` pins the reviewed application commit separately from this coordinator's workflow commit. Owner-only manual execution on main enters the protected `public-image-release` environment. It runs complete Linux/image/resource/lifecycle acceptance before pushing that same image with a short-lived GitHub token. Only that job has package write permission. A separate read-only job validates the public manifest, config, provenance and immutable pull anonymously.

Coordinator runtime packages are published at `ghcr.io/3899178/cloud-mail-build/mail-sync`. The package links to this actual workflow repository. Required original application-source, application-revision and coordinator-revision metadata preserve the full provenance chain.

Standard Ubuntu runners are used without configured long-lived secrets, image artifacts, paid runners or automatic scheduled execution. Workflows do not deploy the website or server.

Passing synthetic CI is evidence only for its named gates. Real provider compatibility, live AWS capacity, production regression and Android readiness require their own acceptance.
