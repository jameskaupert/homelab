FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

RUN apt-get update && \
      apt-get install -y --no-install-recommends \
        curl \
        gpg \
        apt-transport-https \
        wl-clipboard \
        xclip && \
      curl -fsSL
  https://packages.buildkite.com/helm-linux/helm-debian/gpgkey | gpg
   --dearmor > /usr/share/keyrings/helm.gpg && \
      echo "deb [signed-by=/usr/share/keyrings/helm.gpg]
  https://packages.buildkite.com/helm-linux/helm-debian/any/ any
  main" > /etc/apt/sources.list.d/helm-stable-debian.list && \
      apt-get update && \
      apt-get install -y --no-install-recommends helm && \
      rm -rf /var/lib/apt/lists/*

# Install SOPS
RUN curl -LO https://github.com/getsops/sops/releases/download/v3.11.0/sops-v3.11.0.linux.amd64 && \
    mv sops-v3.11.0.linux.amd64 /usr/local/bin/sops && \
    chmod +x /usr/local/bin/sops


COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# Swap to vscode user for remaining user-specific config
USER vscode

RUN helm repo add prometheus-community https://prometheus-community.github.io/helm-charts && \
    helm repo update

# make sure mise is activated in both zsh and bash. 
# Might be overridden by a user's dotfiles.
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(mise activate zsh)"' >> /home/vscode/.zshrc
