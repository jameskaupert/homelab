# devpod-template

Opinionated devpod setup leveraging mise for runtime management. Assumes use of CLI IDE like Neovim, but can use others with devpod config changes like `--ide vscode`.

# Setup
1. Install [DevPod CLI](https://devpod.sh/docs/getting-started/install)
2. Set up devpod provider of your choice
```bash
devpod provider add docker
```
3. Create a new repo based on this template repo
4. Clone the repo locally
5. From the repo root, run
```bash
devpod up . --dotfiles your-repo-here --ide none
```

