# syntax=docker/dockerfile:1
# Microsoft’s devcontainer base already has the VS Code bits, git, sudo, etc.
FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04   # ✅ Noble Numbat 0

#—Fix the “ubuntu user steals UID 1000” bug (until the image is repaired)—
RUN userdel -r ubuntu || true                            # 1

#—System packages—
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends \
        wfuzz wordlists && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# By default Microsoft images drop to user “vscode”.
USER vscode
WORKDIR /workspaces/${GITHUB_REPOSITORY##*/}
