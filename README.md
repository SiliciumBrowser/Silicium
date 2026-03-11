# 🌐 SiliciumBrowser — Chromium-based Browser

A privacy-first, independent Chromium-based browser with built-in Ad-block, VPN/Proxy, and zero Google tracking.

## Architecture

```
ungoogled-chromium (base)
    ├── patches/degoogle/       — Remove all Google services/tracking
    ├── patches/adblock/        — Native ad-blocking engine
    ├── patches/vpn-proxy/      — Built-in VPN/Proxy layer
    └── patches/ui/             — Custom UI/branding
```

## Build Requirements

| Environment     | CPU  | RAM  | Disk  | Usage              |
|----------------|------|------|-------|--------------------|
| GitHub Codespaces | 4   | 8GB  | 32GB  | Full build (~15-18h) |
| GitHub Actions  | 2    | 7GB  | 14GB  | Validate + CI only |

## Quick Start

```bash
# 1. Clone this repo
git clone https://github.com/YOUR_USERNAME/my-browser
cd my-browser

# 2. Setup environment (run inside GitHub Codespaces)
./scripts/setup.sh

# 3. Fetch Chromium source
./scripts/fetch-source.sh

# 4. Apply all patches
./scripts/apply-patches.sh

# 5. Build
./scripts/build.sh
```

## Patch System

Each feature is an isolated set of `.patch` files:

```
patches/
├── degoogle/
│   ├── 001-remove-google-urls.patch
│   ├── 002-disable-safe-browsing.patch
│   ├── 003-remove-signin.patch
│   └── series                          ← patch apply order
├── adblock/
│   ├── 001-adblock-engine-core.patch
│   ├── 002-adblock-url-interceptor.patch
│   └── series
├── vpn-proxy/
│   ├── 001-proxy-config-service.patch
│   ├── 002-wireguard-integration.patch
│   └── series
└── ui/
    ├── 001-branding.patch
    └── series
```

## CI/CD Strategy

- **GitHub Actions** (free runners): Validate patches, lint, test
- **GitHub Codespaces** (60h/month free): Full build + release
- **GitHub Releases**: Host final binaries

## Modules

| Module | Status | Description |
|--------|--------|-------------|
| De-Google | ✅ Base | Remove all Google tracking/services |
| Ad-block | 🚧 WIP | Native engine, no extension needed |
| VPN/Proxy | 🚧 WIP | Built-in proxy/WireGuard support |
| Custom UI | 📋 Planned | Branding + UX improvements |
