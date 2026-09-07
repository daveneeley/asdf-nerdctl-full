# Contributing

Testing Locally:

```shell
asdf plugin test <plugin-name> <plugin-url> [--asdf-tool-version <version>] [--asdf-plugin-gitref <git-ref>] [test-command*]

#
asdf plugin test nerdctl-full https://github.com/daveneeley/asdf-nerdctl-full.git --asdf-tool-version latest "nerdctl -h"

# Rootless containerd and BuildKit are configured automatically during install
asdf install nerdctl-full latest

# Uninstall rootless BuildKit and containerd after testing
nerdctl_full_bin="$(asdf where nerdctl-full)/bin"
"$nerdctl_full_bin/containerd-rootless-setuptool.sh" uninstall-buildkit
"$nerdctl_full_bin/containerd-rootless-setuptool.sh" uninstall
"$nerdctl_full_bin/rootlesskit" rm -rf "$HOME/.local/share/containerd"
```

Tests are automatically run in GitHub Actions on push and PR.
