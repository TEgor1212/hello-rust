# hello-rust 🦀

[![Rust CI/CD](https://github.com/TEgor1212/hello-rust/actions/workflows/ci.yml/badge.svg)](https://github.com/TEgor1212/hello-rust/actions/workflows/ci.yml)

A simple Rust application that prints "Hello, World!" (and then some) — packaged as a minimal Docker image and published to GitHub Container Registry.

## Quick start

### Run locally

```bash
cargo run
```

### Run tests

```bash
cargo test
```

## Docker

### Pull the image

```bash
docker pull ghcr.io/TEgor1212/hello-rust:latest
```

### Run the container

```bash
docker run --rm ghcr.io/TEgor1212/hello-rust:latest
```

Pass command-line arguments:

```bash
docker run --rm ghcr.io/TEgor1212/hello-rust:latest foo bar
```

## CI/CD

On every push to `main`, GitHub Actions:

1. Lints the code with Clippy
2. Checks formatting with `cargo fmt`
3. Runs tests
4. Builds a release binary
5. Builds a **multi-stage Docker image** and pushes it to `ghcr.io/TEgor1212/hello-rust`

The Docker image is built from a **distroless-like** `debian:stable-slim` base and runs as a non-root user.

### Tags published

| Tag | When |
|-----|------|
| `latest` | On push to `main` |
| `{short-sha}` | Every CI run on `main` |