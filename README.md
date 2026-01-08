# homelab
Kubernetes homelab running k3s on a Raspberry Pi.  My tinkering playground for exploring Kubernetes and running apps that improve my life.

## DevPods Devcontainer Setup
I manage updates from within a devcontainer based on [devpod.sh](https://devpod.sh). Example setup below assumes you want to use something like Neovim from the CLI.

1. Install [DevPod CLI](https://devpod.sh/docs/getting-started/install)
2. Set up devpod provider of your choice
```bash
devpod provider add docker
```
3. Clone the repo locally
4. From the repo root, run
```bash
devpod up . --dotfiles your-repo-here --ide none
```

## Current Apps
- Bookmark Management
  - Linkding
- Music
  - Navidrome
  - Feishin
  - Filebrowser
- Audiobooks
  - Audiobookshelf

