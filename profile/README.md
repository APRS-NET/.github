<div align="center">

<img src="assets/aprs-net-icon.svg" alt="APRS.NET icon: a map pin broadcasting radio waves" width="120" height="120">

# APRS.NET

**Modern, async-first .NET tooling for amateur radio APRS.**

[Projects](#projects) · [Getting started](#getting-started) · [Contributing](#contributing) · [Licensing](#licensing)

</div>

---

> [!WARNING]
> **Alpha software.** Everything in this organization is pre-release (`0.x.y-alpha.N`) until at least v1.0.0. APIs,
> behaviour, settings and package names can change between any two releases without notice. Please do not depend on it
> in production yet.

## About

APRS.NET is a small family of open-source projects for the
[Automatic Packet Reporting System (APRS)](https://en.wikipedia.org/wiki/Automatic_Packet_Reporting_System), the
amateur radio protocol for sharing positions, weather, messages and telemetry. The goal is a clean, well-tested,
dependency-light foundation in C#, plus modern applications built on top of it.

## Projects

### [APRS.NET](https://github.com/APRS-NET/APRS.NET): the libraries

An async-first .NET library family for APRS: parse and build every common packet type, connect to APRS-IS, and bridge
radios and clients over KISS, APRS-IS and WebSocket. It covers the APRS-IS client (verified sending, TLS, automatic
reconnects), AX.25 and KISS TNCs over TCP or serial, messaging with acks and retries, GPS through gpsd or NMEA, beacon
schedules including SmartBeaconing, a local APRS-IS gateway, a receive-only or two-way IGate, and a digipeater.

| Package | Purpose |
| --- | --- |
| `AprsNet.Packets` | Packet models, parser and encoder (no I/O) |
| `AprsNet.Packets.Json` | Packets as documented JSON, for web apps, logs and pipes |
| `AprsNet.AprsIsTcpClient` | APRS-IS client |
| `AprsNet.Filters` | APRS-IS filters: build them from typed terms and evaluate them locally |
| `AprsNet.Symbols` | Symbol meanings and SVG symbol images |
| `AprsNet.DeviceId` | Device and program identification from the aprs-deviceid list |
| `AprsNet.Ax25` | AX.25 UI frames and the digipeater rules |
| `AprsNet.Kiss`, `AprsNet.Kiss.Serial` | KISS TNCs over TCP, any stream or a serial port, and a KISS TCP server |
| `AprsNet.Messaging` | Message conversations: IDs, retries until an ack, reply-acks |
| `AprsNet.Beacons` | Beacon schedules, SmartBeaconing and dead reckoning |
| `AprsNet.Gps` | GPS through gpsd, with reconnects |
| `AprsNet.IGate` | IGate rules in both directions |
| `AprsNet.Gateway` | A local APRS-IS server fed by APRS-IS and KISS TNCs |
| `AprsNet.Corpus` | Packet capture format and anonymizer for test corpora |
| `AprsNet.Extensions.DependencyInjection` | Register an APRS-IS connection from configuration |

It also ships `aprscli`, a command-line tool (and container image) that can run the gateway, share a TNC, and run as
systemd services. MIT licensed.

### [AprsMap](https://github.com/APRS-NET/AprsMap): the map client

An APRS map client built on .NET 10 and Avalonia. One UI and one engine, delivered as a native desktop app (Windows,
Linux, macOS) and as a web app served by a Docker gateway. It receives and transmits over APRS-IS and your own TNCs, and
shows stations on a live map with tracks, RF paths and dead-reckoned positions, alongside station and packet lists,
station details and a dashboard. Licensed operators can beacon (fixed, decaying or SmartBeaconing from a GPS), send
messages, objects and items, digipeat, and run a two-way IGate.

The feature set is a clean-room reimplementation of the functionality of APRSIS32, with a modern UI. AGPL-3.0, with
its engine and docs under MIT.

## Getting started

Install the libraries (pre-releases, so pass `--prerelease`):

```bash
dotnet add package AprsNet.Packets --prerelease
dotnet add package AprsNet.AprsIsTcpClient --prerelease
dotnet tool install --global AprsNet.AprsIsCli --prerelease   # the aprscli tool
```

Try the AprsMap web app with Docker:

```bash
docker run -p 8080:8080 ghcr.io/aprs-net/aprsmap:alpha
```

Then open <http://localhost:8080>. Without a passcode, AprsMap logs in to APRS-IS receive-only and transmits nothing.
Self-contained desktop builds for Windows, Linux and macOS (x64 and arm64) are on the
[AprsMap releases page](https://github.com/APRS-NET/AprsMap/releases).

Guides for TNCs, the gateway, containers and Linux services are in the
[APRS.NET docs](https://github.com/APRS-NET/APRS.NET/tree/main/docs/guides).

## Contributing

Issues and pull requests are welcome in each repository. Before you start:

- Build and test with `dotnet tool restore`, `dotnet build` and `dotnet test`.
- Code is formatted with [CSharpier](https://csharpier.com), and CI fails on unformatted files. Enable the pre-commit
  hook once per clone with `git config core.hooksPath .githooks`.
- Warnings are treated as errors, banned APIs are enforced by analyzers, and CI enforces minimum code coverage (85%
  line, 80% branch).
- Check each project's `docs/` folder for architecture and scope notes before proposing larger changes. AprsMap follows
  a [clean-room process](https://github.com/APRS-NET/AprsMap/blob/main/docs/clean-room.md); please read it before
  contributing there.

## Licensing

APRS.NET is MIT licensed. AprsMap is AGPL-3.0-only, with its engine (`AprsMap.Contracts`, `AprsMap.Core`,
`AprsMap.Client.Remote`, `AprsMap.Tiles`) and docs under MIT so other tools can reuse them. See each repository's
`LICENSE` and, for AprsMap, [`LICENSING.md`](https://github.com/APRS-NET/AprsMap/blob/main/LICENSING.md).

## AI assistance

These projects are developed with an AI coding assistant (Claude Code) working alongside the maintainer, who reviews
and commits every change. Each repository includes an `AI-DECLARATION.md` with the details.

## Not affiliated

APRS.NET is an independent open-source project. The APRS name is used here only to describe the protocol these
projects implement. APRSIS32 is the work of Lynn Deffenbaugh, KJ4ERJ; AprsMap is unaffiliated with it and uses none of
its code or assets.

---

<div align="center">

73 and happy tracking.

</div>
