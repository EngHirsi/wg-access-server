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

## License

MIT. This project is based on [Place1/wg-access-server](https://github.com/Place1/wg-access-server). Retain the upstream copyright notice and MIT license text when redistributing upstream code or substantial portions of it.
