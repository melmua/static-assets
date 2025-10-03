# CI Base Docker Image Usage

## Overview

This Docker image provides a comprehensive CI/CD environment with Go, Node.js, and essential development tools pre-installed. It's designed for building and testing applications in GitHub Actions and other CI/CD pipelines.

## Image Details

- **Base Image**: `golang:1.24.6`
- **Registry**: `ghcr.io/[owner]/ci-base`
- **Architectures**: `linux/amd64`, `linux/arm64`
- **Default Shell**: `zsh`

## Pre-installed Tools

### Go Development
- **Go Version**: 1.24.6
- **goimports**: v0.37.0 (code formatting)
- **golangci-lint**: v1.61.0 (linting)
- **govulncheck**: latest (vulnerability scanning)

### Node.js Development
- **Node.js Version**: 20.18.0
- **Package Manager**: pnpm v9.14.4
- **Architecture Support**: amd64, arm64

### System Tools
- **Shell**: zsh (default)
- **Task Runner**: Just (command runner)
- **Version Control**: git
- **Utilities**: curl, wget, gnupg, xz-utils

## Usage Examples

### Basic Usage
```bash
# Pull the latest image
docker pull ghcr.io/melmua/ci-base:latest

# Run a simple command
docker run --rm ghcr.io/melmua/ci-base:latest go version

# Run with interactive shell
docker run -it ghcr.io/melmua/ci-base:latest /usr/bin/zsh
```

### In GitHub Actions
```yaml
- name: Run tests
  uses: docker://ghcr.io/melmua/ci-base:latest
  with:
    args: go test ./...
```