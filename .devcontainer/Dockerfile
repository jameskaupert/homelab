FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

# Install Helm
RUN sudo apt-get update && \
    sudo apt-get install -y curl gpg apt-transport-https && \
    curl -fsSL https://packages.buildkite.com/helm-linux/helm-debian/gpgkey | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null && \
    echo "deb [signed-by=/usr/share/keyrings/helm.gpg] https://packages.buildkite.com/helm-linux/helm-debian/any/ any main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list && \
    sudo apt-get update && \
    sudo apt-get install -y helm


COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# Swap to vscode user for remaining user-specific config
USER vscode

RUN helm repo add prometheus-community https://prometheus-community.github.io/helm-charts && \
    helm repo update

# make sure mise is activated in both zsh and bash. 
# Might be overridden by a user's dotfiles.
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(mise activate zsh)"' >> /home/vscode/.zshrc
