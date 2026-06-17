# Panama Linux &nbsp; [![bluebuild build badge](https://github.com/sparkwave2/panama-linux/actions/workflows/build.yml/badge.svg)](https://github.com/sparkwave2/panama-linux/actions/workflows/build.yml)

Panama is a Fedora Kinoite-based atomic Linux distro made with BlueBuild. It's meant to be an alternative to Bazzite.

Supports amd64 and ARM. Requires an AMD, Intel or modern Nvidia GPU.

List of features:
- KDE Plasma desktop
- Steam preinstalled natively
- Includes Waterfox, Flatseal, Lutris, RetroArch, VSCodium, Vesktop and ProtonUp Qt flatpaks by default
- Includes Cascadia Code, Fira Code and OpenDyslexic fonts by default
- Bazzite kernel with various gaming improvements
- Customized kernel flags for gaming performance
- Openrazer driver for Razer devices
- Drivers for various gaming peripherals
- Drivers for Framework and System76 laptop hardware
- Improved Xbox controller support
- Nvidia open kernel driver preinstalled
- Pipewire, a flexible and improved sound engine
- ZSH, an improved terminal shell
- TigerVNC Server for VNC uses, disabled by default

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/sparkwave2/panama-linux:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/sparkwave2/panama-linux:latest
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
cosign verify --key cosign.pub ghcr.io/sparkwave2/panama-linux
```
