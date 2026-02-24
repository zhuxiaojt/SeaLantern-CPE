<div align="center">
	<img src="src/assets/logo.svg" alt="logo" width="200" height="200">

# Sea Lantern CPE (海晶灯社区平台版)

A Minecraft Server Manager based on Tauri 2 + Rust + Vue 3

| [![github-stars](https://img.shields.io/github/stars/zhuxiaojt/SeaLantern-CPE?style=flat&logo=github&label=Stars)](https://github.com/zhuxiaojt/SeaLantern-CPE/stargazers) | [![github-forks](https://img.shields.io/github/forks/zhuxiaojt/SeaLantern-CPE?style=flat&logo=github&label=Forks)](https://github.com/zhuxiaojt/SeaLantern-CPE/network/members) | [![github-latest](https://img.shields.io/github/v/release/zhuxiaojt/SeaLantern-CPE?style=flat&logo=github&label=Latest%20version)](https://github.com/zhuxiaojt/SeaLantern-CPE/releases/latest)                                                                                    |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

<kbd>[简体中文](README.md)</kbd> <kbd>English</kbd>

---

</div>

## What can it do?

- Logs and load at the control panel in real time; send commands to the server directly
- Edit server.properties graphically, without browsing directories
- Manage whitelists, bans and OPs in switches
- The server shuts down automatically when you close the app, so no saves are damaged.
- Check for and download updates in one click

## Quick Start

Download the software from [Releases](https://github.com/zhuxiaojt/SeaLantern-CPE/releases/latest);

Import a server .jar, choose a Java version, then click Start. It's that simple.

## Development

You'll need Node.js 20+ and Rust 1.70+.

```bash
git clone https://github.com/zhuxiaojt/SeaLantern-CPE.git
cd SeaLantern-CPE
npm install
npm run tauri dev
```

On some Linux distributions, such as Arch, running `npm run tauri dev` directly may not compile successfully. Please check if your dependency libraries are complete. It is recommended to use your package manager to install `Tauri` dependencies beforehand when running the above command to avoid missing dependency issues. [Click here to go to "Tauri | Prerequisites"](https://tauri.app/start/prerequisites/#linux)

Build release:

```bash
npm run tauri build
```

Built binaries are in `src-tauri/target/release/bundle/`.

### Code Quality Check

Before your PR, we encourage you to run the commands below to check the code's quality:

- For frontend

> ```bash
> # Code Quality Check
> npm run lint
>
> # Fix fixable problems
> npm run lint:fix
>
> # Format code
> npm run fmt
>
> # Check format
> npm run fmt:check
> ```

- For backend

> ```bash
> # Check format
> cargo fmt --all -- --check
>
> # Run Clippy check
> cargo clippy --workspace -- -D warnings
>
> # Format code
> cargo fmt --all
> ```

CI automated checks are set up to ensure that all submitted code meets the standards.

## Tech Stack

- **Frontend**: Vue 3 + TypeScript + Vite + Pinia
- **Backend**: Rust + Tauri 2
- **Style**: CSS
- **Communicate**: Tauri invoke (The frontend calls Rust functions and receives the results)

No Electron, no Node backend, no Webpack. Launch fast, size small, RAM saved.

### Project Structure

See [Project Structure](docs/STRUCTURE-en.md).

## Planned Features

Placeholders have been reserved for these features with existing code
skeletons—waiting for your contributions:

- Download Center - Download server cores, Minecraft versions, plugins and mods
- Backup Management - Incremental backup and restore of save files
- Intranet Penetration - FRP integration
- Scheduled Tasks - Automatic restarts, scheduled backups, and scheduled commands
- Resource Management - Search and install plugins/mods from Modrinth & CurseForge

## Contributing

Contributions are welcome! Before you start, please read the [Contributing Guidelines](docs/CONTRIBUTING-en.md) to understand code standards and development workflows.

GUI modifications are also OK!

Colors are managed via CSS variables —
components are modular —
change any part you don't like.

Want to create a theme/skin? Go for it;
want to completely redesign the layout? That's fine!

### How to Contribute

1. Fork the repository
2. Create a branch and implement your changes
3. Submit a Pull Request
4. Your name will be added to the contributor wall

You don't need coding skills to contribute. Just suggest new features you want or share a UI sketch — they all count as contributions!

### Add a new function

If you are going to add a "Backup Management":

#### Backend

1. Create `backup_manager.rs` under `src-tauri/src/services/`, code the logic
2. Create `backup.rs` under `src-tauri/src/commands/`, code with Tauri
3. Add `pub mod backup` in `commands/mod.rs`
4. Register the command in the `generate_handler!` macro under `lib.rs`

#### Frontend

1. Create `backup.ts` under `src/api/`, encapsulate invokes
2. Create `BackupView.vue` under `src/views/`, make the page
3. Add routes in `src/router/index.ts`
4. Add an item to the `navItems` array in `AppSidebar.vue`

The frontend and backend each have 3 files, plus one line each for the router and the sidebar.

### i18n — Internationalization Guide

Sea Lantern CPE supports multiple languages, including Simplified Chinese, Traditional Chinese and English. See the i18n guide: [src/language/README-en.md](src/language/README-en.md)

## License

[GNU General Public License v3.0](LICENSE)

This project is a derivative work of [SeaLantern](https://github.com/SeaLantern-Studio/SeaLantern), following the GPLv3 license.

## Acknowledgments

Sea Lantern CPE is an open source project under the GPLv3 license.

Minecraft is a trademark of Mojang AB.
This project is not approved or associated with Mojang or Microsoft.

"We've built the framework — the soul is up to you."
