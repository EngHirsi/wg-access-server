# wg-access-server

Connecting devices to a WireGuard VPN means configuring the server, registering each device, and distributing connection settings. wg-access-server puts the VPN server and a device management web UI together, with user authentication and QR codes for device setup.

## Features

- Authenticate users before they register devices through the web UI.
- Register devices in one click and provide QR codes for mobile setup.
- Connect macOS, Linux, Windows, iOS, and Android devices with WireGuard clients.
- Configure network isolation modes to control VPN connectivity.
- Run the WireGuard server and device management UI from a single binary.

## Installation

The backend is written in Go; the frontend uses React and TypeScript. To run from source, install Go, Node.js, and npm. The backend also needs a Linux environment with `iptables` and `ip`, plus permission to configure network interfaces.

From the root of your source checkout, install the frontend dependencies:

```bash
cd website && npm install
```

There is no npm-based server installation documented here. npm manages the web frontend; Go runs the VPN backend.

## Usage

For local development, start the frontend from the repository root:

```bash
cd website && npm start
```

In a second terminal, start the backend from the repository root:

```bash
sudo go run ./main.go
```

Open http://localhost:3000. The frontend proxies API requests to the backend on port 8000. The backend needs elevated privileges because it configures VPN networking through `iptables` and `ip`.

Use the web UI to sign in and register a device. On a phone, open the UI through the development machine's LAN address and scan the device QR code with a WireGuard client.

**This development setup uses in-memory storage and generated WireGuard keys.** Do not treat it as a persistent deployment.

<!-- seorepo:network:start -->
## More tools from our network

- [**octo-cli**](https://github.com/boostlyapi/octo-cli) — CLI на Go для публикации данных из PostgreSQL, MSSQL и MySQL через бессерверные веб-сервисы в OpenFaaS или Knative. Конфигурация сервиса задаётся в YAML.
- [**tool**](https://github.com/boostlyapi/tool) — CLI на Go для Apache Kafka: чтение и отправка сообщений в JSON, просмотр топиков, управление смещениями consumer groups и базовое администрирование.
- [**docker-ikev2-vpn-server**](https://github.com/Cabral-it/docker-ikev2-vpn-server) — Docker-based IKEv2 VPN server with shared-secret authentication and .mobileconfig generation for iOS and macOS, based on gaomd/docker-ikev2-vpn-server.
- [**akrobateo**](https://github.com/Dyooooou/akrobateo) — A Go Kubernetes operator that exposes LoadBalancer services through node hostPorts using DaemonSets and synchronizes their load balancer addresses.
- [**node-hnsn**](https://github.com/ghb13/node-hnsn) — A TypeScript node for decentralized document timestamping with Bitcoin and IPFS, with an HTTP API for signed work claims and file uploads.
- [**minter-go-node**](https://github.com/maxwildcat/minter-go-node) — Go implementation of a Minter blockchain node for a network of custom coins, rewards, and loyalty points, based on MinterTeam/minter-go-node.
<!-- seorepo:network:end -->

## License

MIT. This project is based on [Place1/wg-access-server](https://github.com/Place1/wg-access-server). Retain the upstream copyright notice and MIT license text when redistributing upstream code or substantial portions of it.
