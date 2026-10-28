<div align="center">

<img src="assets/aprs-net-icon.svg" alt="APRS.NET icon: a map pin broadcasting radio waves" width="120" height="120">

# APRS.NET

**Modern, async-first .NET tooling for amateur radio APRS.**

[Libraries](#libraries) · [Apps](#apps) · [Getting started](#getting-started) · [Contributing](#contributing) · [Licensing](#licensing)

</div>

---

> [!WARNING]
> **Alpha software.** Everything in this organization is pre-release (`0.x.y-alpha.N`) until at least v1.0.0. APIs, behaviour and package names can change between any two releases without notice. Please do not depend on it in production yet.

## About

APRS.NET is a small family of open-source projects for the [Automatic Packet Reporting System (APRS)](https://en.wikipedia.org/wiki/Automatic_Packet_Reporting_System), the amateur radio protocol for sharing positions, weather, messages and telemetry. The goal is a clean, well-tested, dependency-light foundation in C#, plus modern applications built on top of it.

## Projects

### Libraries

| Project | What it is | Licence |
| --- | --- | --- |
| [**APRS.NET**](https://github.com/APRS-NET/APRS.NET) | An async-first library family for APRS. Parse and build packets, connect to APRS-IS, and (planned) bridge radios and clients over KISS, TCP and WebSocket. | MIT |

Packages published to nuget.org as pre-releases:

| Package | Purpose |
| --- | --- |
| `AprsNet.Packets` | Packet models, parser and encoder (no I/O) |
| `AprsNet.AprsIsTcpClient` | APRS-IS client |
| `AprsNet.Symbols` | Symbol meanings and SVG symbol images |

### Apps

| Project | What it is | Licence |
| --- | --- | --- |
| [**AprsMap**](https://github.com/APRS-NET/AprsMap) | An APRS map client built on .NET 10 and Avalonia. One UI and one engine, delivered as a native desktop app (Windows, Linux, macOS) and as a web app served by a Docker gateway. Currently in early foundations: it connects to APRS-IS and lists live packets, with the map still to come. | AGPL-3.0 (engine and docs MIT) |

## Getting started

Install the libraries (pre-releases, so pass `--prerelease`):

```bash
dotnet add package AprsNet.Packets --prerelease
dotnet add package AprsNet.AprsIsTcpClient --prerelease
dotnet add package AprsNet.Symbols --prerelease
```

Try the AprsMap web app with Docker:

```bash
docker run -p 8080:8080 ghcr.io/aprs-net/aprsmap:alpha
```

Then open <http://localhost:8080>. Without a passcode, AprsMap logs in to APRS-IS receive-only and transmits nothing. Desktop builds are on the [AprsMap releases page](https://github.com/APRS-NET/AprsMap/releases).

## Contributing

Issues and pull requests are welcome in each repository. Before you start:

- Build and test with `dotnet tool restore`, `dotnet build` and `dotnet test`.
- Code is formatted with [CSharpier](https://csharpier.com), and CI fails on unformatted files. Enable the pre-commit hook once per clone with `git config core.hooksPath .githooks`.
- Warnings are treated as errors, and CI enforces minimum code coverage.
- Check each project's `docs/` folder for architecture and scope notes before proposing larger changes.

## Licensing

APRS.NET is MIT licensed. AprsMap is AGPL-3.0-only, with its engine and docs under MIT so other tools can reuse them. See each repository's `LICENSE` and, for AprsMap, `LICENSING.md`.

## AI assistance

These projects are developed with an AI coding assistant working alongside the maintainer, who reviews and commits every change. Each repository includes an `AI-DECLARATION.md` with the details.

## Not affiliated

APRS.NET is an independent open-source project. The APRS name is used here only to describe the protocol these projects implement.

---

<div align="center">

73 and happy tracking.

</div>
