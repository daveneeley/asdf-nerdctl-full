<div align="center">

# asdf-nerdctl-full [![Build](https://github.com/daveneeley/asdf-nerdctl-full/actions/workflows/build.yml/badge.svg)](https://github.com/daveneeley/asdf-nerdctl-full/actions/workflows/build.yml) [![Lint](https://github.com/daveneeley/asdf-nerdctl-full/actions/workflows/lint.yml/badge.svg)](https://github.com/daveneeley/asdf-nerdctl-full/actions/workflows/lint.yml)


[nerdctl-full](https://github.com/daveneeley/asdf-nerdctl-full) plugin for the [asdf version manager](https://asdf-vm.com).

</div>

# Contents

- [asdf-nerdctl-full  ](#asdf-nerdctl-full--)
- [Contents](#contents)
- [Dependencies](#dependencies)
- [Install](#install)
- [Additional Commands](#additional-commands)
- [Contributing](#contributing)
- [License](#license)

# Dependencies

- `bash`, `curl`, `tar`: generic POSIX utilities.
- `containerd`: responsible for storing and retrieving docker image layers

# Install

Plugin:

```shell
asdf plugin add nerdctl-full
# or
asdf plugin add nerdctl-full https://github.com/daveneeley/asdf-nerdctl-full.git
```

nerdctl-full:

```shell
# Show all installable versions
asdf list-all nerdctl-full

# Install specific version
asdf install nerdctl-full latest

# Set a version globally (on your ~/.tool-versions file)
asdf global nerdctl-full latest

# Now nerdctl-full commands are available
nerdctl -h
```

Check [asdf](https://github.com/asdf-vm/asdf) readme for more instructions on how to
install & manage versions.

# Additional Commands

```shell
# Set CNI_PATH while installing rootless containerd and BuildKit
cni_path="$(asdf where nerdctl-full)/bin/cni"
CNI_PATH="$cni_path" containerd-rootless-setuptool.sh install
CNI_PATH="$cni_path" containerd-rootless-setuptool.sh install-buildkit

# Persist CNI_PATH in both user systemd services
mkdir -p ~/.config/systemd/user/containerd.service.d
mkdir -p ~/.config/systemd/user/buildkit.service.d
printf '[Service]\nEnvironment=CNI_PATH=%s\n' "$cni_path" \
  >~/.config/systemd/user/containerd.service.d/nerdctl-full.conf
printf '[Service]\nEnvironment=CNI_PATH=%s\n' "$cni_path" \
  >~/.config/systemd/user/buildkit.service.d/nerdctl-full.conf
systemctl --user daemon-reload

# Manage containerd and BuildKit
systemctl --user start containerd.service
systemctl --user stop containerd.service
systemctl --user start buildkit.service
systemctl --user stop buildkit.service

```

# Contributing

Contributions of any kind welcome! See the [contributing guide](contributing.md).

[Thanks goes to these contributors](https://github.com/daveneeley/asdf-nerdctl-full/graphs/contributors)!

# License

See [LICENSE](LICENSE) © [Dave Neeley](https://github.com/daveneeley/)
