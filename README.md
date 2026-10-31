# Cloud Mail Linux build coordination

This public repository coordinates secret-free Linux acceptance for the application at https://github.com/3899178/cloud-mail.

The workflow checks out an explicitly pinned application commit and runs that source's existing deploy/ci.sh, including its runtime-image and 320MiB resource gates. Logs identify both the application source commit and this coordinator commit.

Only the repository owner can manually trigger the initial workflow on main. It uses a standard Ubuntu runner with read-only repository permissions and no configured secrets. It does not deploy the service, publish images or upload artifacts.

A passing build is evidence for the named synthetic Linux gates. It does not establish real mailbox compatibility, live server capacity, production acceptance or Android readiness. The application repository and its existing history remain the source of product development.
