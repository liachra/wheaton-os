# wheaton-os &nbsp; [![bluebuild build badge](https://github.com/liachra/wheaton-os/actions/workflows/build.yml/badge.svg)](https://github.com/liachra/wheaton-os/actions/workflows/build.yml)
A Linux image based distro with sensible & Quality of Life changes.
There are two images
  - wheaton-os **[MAIN]**
    *A general purpose distro suitible for everyday tasks & gaming. Suitible for everyone.*
  - wheaton-os:opsec ***[ALPHA]***
    *A security focused distro based on the [SecureBlue](secureblue/secureblue) image. Has a strong security focused setup with hard security changes made to Fedora and the Linux kernel. This image is a dev image focused for technical users who require extra sensible hardening to their operating environment without going to the extreme. Only use this image if you have an stronger than average understanding of linux sysops.[[1]](1)*
    
    [1]*This image is intended to be merged into the main image(s), the plan is to build user friendly defaults for general purpose use with a GUI front end for easy modifications ontop of SecureBlue's ujust commands.

----
# BlueBuild default readme
See the [BlueBuild docs](https://blue-build.org/how-to/setup/) for quick setup instructions for setting up your own repository based on this template.

After setup, it is recommended you update this README to describe your custom image.

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/liachra/wheaton-os:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/liachra/wheaton-os:latest
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
cosign verify --key cosign.pub ghcr.io/liachra/wheaton-os
```

## Upstream Credits
[BlueBuild](https://blue-build.org)<br>
[Universal Blue & Bazzite](bazzite.gg)<br>
[SecureBlue](https://secureblue.dev)<br>
[Fedora](https://fedoraproject.org)