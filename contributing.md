# Contributing

Testing Locally:

```shell
asdf plugin test <plugin-name> <plugin-url> [--asdf-tool-version <version>] [--asdf-plugin-gitref <git-ref>] [test-command*]

#
asdf plugin test nerdctl-full https://github.com/daveneeley/asdf-nerdctl-full.git --asdf-tool-version latest "nerdctl -h"

# Set CNI_PATH while installing rootless containerd and BuildKit
cni_path="$(asdf where nerdctl-full)/bin/cni"
CNI_PATH="$cni_path" containerd-rootless-setuptool.sh install
CNI_PATH="$cni_path" containerd-rootless-setuptool.sh install-buildkit
```

Tests are automatically run in GitHub Actions on push and PR.
