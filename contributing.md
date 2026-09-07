# Contributing

Testing Locally:

```shell
asdf plugin test <plugin-name> <plugin-url> [--asdf-tool-version <version>] [--asdf-plugin-gitref <git-ref>] [test-command*]

#
asdf plugin test nerdctl-full https://github.com/daveneeley/asdf-nerdctl-full.git --asdf-tool-version latest "nerdctl -h"

# Install rootless containerd and BuildKit
containerd-rootless-setuptool.sh install
containerd-rootless-setuptool.sh install-buildkit
```

Tests are automatically run in GitHub Actions on push and PR.
