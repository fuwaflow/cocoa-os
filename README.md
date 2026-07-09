# usagi &nbsp; [![bluebuild build badge](https://github.com/fuwaflow/usagi/actions/workflows/build.yml/badge.svg)](https://github.com/fuwaflow/usagi/actions/workflows/build.yml)

a fedora atomic image with pantheon and batteries included

made with [BlueBuild](https://blue-build.org/) 

thanks to https://github.com/garaevdi/prosto/

## current bugs
- ~~screen recording portal non functional~~ fixed as of 10 July 2026
- ~~some icons (symbolics?) are missing and idk why~~ fixed as of 10 July 2026
- trying to switch desktops with super left right switches ttys but only sometimes idk what causes it (maybe still happening as of 10 July 2026, cannot tell, need to reproduce)
- wingpanel and the dock take a few seconds to show up, still an issue as of 10 July 2026

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/fuwaflow/usagi:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/fuwaflow/usagi:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/how-to/generate-iso/#_top). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/fuwaflow/usagi
```
