# OpenCodeReview snap

[![opencodereview](https://snapcraft.io/opencodereview/badge.svg)](https://snapcraft.io/opencodereview)

Snap packaging for [OpenCodeReview](https://github.com/alibaba/open-code-review), an AI-powered code review tool with configurable rules, saved sessions and a local review viewer.

Unofficial build, not affiliated with or endorsed by Alibaba or the OpenCodeReview project.

## Build

```bash
snapcraft pack
```

## Install and try

<a href="https://snapcraft.io/opencodereview"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install opencodereview
sudo snap connect opencodereview:removable-media   # optional: /media, /mnt
opencodereview config provider
opencodereview config model
cd ~/my-project
opencodereview review
```

The snap includes Git. Configure a model provider before reviewing code, or use `opencodereview delegate preview` with your AI agent.

To use the upstream `ocr` command name, including in agent integrations:

```bash
sudo snap alias opencodereview ocr
```

View saved reviews with `opencodereview viewer --open=never`, then open the URL printed in the terminal. Configuration and sessions live under `~/snap/opencodereview/common/.opencodereview`.

## Known limitations

- Projects must be in a non-hidden home folder or connected removable storage. Hidden files directly under your home directory are inaccessible.
- Host credentials and programs are not shared with the snap. Use provider configuration or environment variables, and HTTP MCP servers instead of host commands.
- Open browser URLs manually. For ChatGPT login, use `opencodereview auth login --provider chatgpt --no-browser`.

## Update to a new upstream release

Change `version` in `snap/snapcraft.yaml`, then rebuild.

## Automation

Builds, publishing, and dependency updates use [snap-automation](https://github.com/sidalit/snap-automation).

## License

The packaging is MIT-licensed (see `LICENSE`). OpenCodeReview is Apache-2.0-licensed; Git and the other dependencies carry their own licenses.
