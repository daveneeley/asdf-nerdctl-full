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
# Get help on containerd
asdf cmd nerdctl-full help

# Install containerd with systemd
asdf cmd nerdctl-full containerd-systemd

# Install containerd for openrc
asdf cmd nerdctl-full containerd-openrc

# Start containerd in foreground
asdf cmd nerdctl-full containerd-start

# Stop or cleanup containerd started in foreground
asdf cmd nerdctl-full containerd-stop

```

# Contributing

Contributions of any kind welcome! See the [contributing guide](contributing.md).

[Thanks goes to these contributors](https://github.com/daveneeley/asdf-nerdctl-full/graphs/contributors)!

# License

See [LICENSE](LICENSE) © [Dave Neeley](https://github.com/daveneeley/)
