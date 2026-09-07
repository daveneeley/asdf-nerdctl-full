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
# Rootless containerd and BuildKit are configured automatically during install
asdf install nerdctl-full latest

# Manage containerd and BuildKit
systemctl --user start containerd.service
systemctl --user stop containerd.service
systemctl --user start buildkit.service
systemctl --user stop buildkit.service

# Uninstall rootless BuildKit and containerd
nerdctl_full_bin="$(asdf where nerdctl-full)/bin"
"$nerdctl_full_bin/containerd-rootless-setuptool.sh" uninstall-buildkit
"$nerdctl_full_bin/rootlesskit" rm -rf "$HOME/.local/share/buildkit"
"$nerdctl_full_bin/containerd-rootless-setuptool.sh" uninstall
"$nerdctl_full_bin/rootlesskit" rm -rf "$HOME/.local/share/containerd"

```

# Testing Plugin Changes

The installer creates fixed user systemd units named `containerd.service` and
`buildkit.service`. Do not use `asdf plugin test`, because its temporary
`asdf-test-nerdctl-full` plugin shares those units with `nerdctl-full`.

Commit and push changes to a branch before testing. Update the existing plugin
in place and install the latest nerdctl-full release:

```shell
branch="v0.19"
git add .
git commit -m "describe the change"
git push origin "$branch"

asdf plugin update nerdctl-full "$branch"
asdf uninstall nerdctl-full 2.3.5
asdf install nerdctl-full latest
nerdctl --version
```

If a previous test left services or data behind, clean them up before retrying:

```shell
nerdctl_full_bin="$(asdf where nerdctl-full)/bin"
"$nerdctl_full_bin/containerd-rootless-setuptool.sh" uninstall-buildkit || true
"$nerdctl_full_bin/containerd-rootless-setuptool.sh" uninstall || true
"$nerdctl_full_bin/rootlesskit" rm -rf "$HOME/.local/share/buildkit" || true
"$nerdctl_full_bin/rootlesskit" rm -rf "$HOME/.local/share/containerd" || true
systemctl --user daemon-reload
```

# Contributing

Contributions of any kind welcome! See the [contributing guide](contributing.md).

[Thanks goes to these contributors](https://github.com/daveneeley/asdf-nerdctl-full/graphs/contributors)!

# License

See [LICENSE](LICENSE) © [Dave Neeley](https://github.com/daveneeley/)
