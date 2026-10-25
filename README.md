<div align="center">

<img src="snap/gui/opencodereview.png" alt="OpenCodeReview logo" width="128" />

# OpenCodeReview

**Review code with AI providers from your terminal.**

[![opencodereview](https://snapcraft.io/opencodereview/badge.svg)](https://snapcraft.io/opencodereview)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [OpenCodeReview](https://github.com/alibaba/open-code-review), an AI code review tool with saved sessions and a local review viewer.

</div>

---

## Getting Started

<a href="https://snapcraft.io/opencodereview"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install opencodereview
sudo snap alias opencodereview.ocr ocr
```

The alias enables the upstream `ocr` command; otherwise use `opencodereview.ocr`. Configure a provider below, then review your project:

```bash
cd ~/my-project
ocr review
```

## Configure

This snap has no `snap set` options. For OpenRouter, replace the model and API key placeholders:

```bash
ocr config set provider openrouter
ocr config set model 'YOUR_MODEL_ID'
ocr config set providers.openrouter.api_key 'YOUR_KEY'
```

Alternatively, use `ocr auth login --provider chatgpt`; add `--no-browser` when browser opening is unavailable. Interactive configuration is available through `ocr config provider` and `ocr config model`.

Settings are saved in `~/snap/opencodereview/common/.opencodereview/config.json`; sessions share that directory. View saved reviews with `ocr viewer`, or use `ocr delegate preview` with your AI agent.

```bash
sudo snap connect opencodereview:removable-media   # optional: /media, /mnt
```

## Limitations

- Projects must be in a non-hidden home folder or connected removable storage. Hidden files directly under your home are inaccessible.
- Host credentials and programs are not shared with the snap. Configure providers inside the snap or pass credentials through environment variables.
- Use HTTP MCP servers instead of MCP commands that require host-installed programs.

## Build

```bash
git clone https://github.com/sidalit/opencodereview-snap.git
cd opencodereview-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/opencodereview-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/alibaba/open-code-review/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/opencodereview-snap/blob/main/LICENSE).
