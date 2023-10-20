![plugin-shell](https://github.com/tauri-apps/plugins-workspace/raw/v2/plugins/shell/banner.png)

Access the system shell. Allows you to spawn child processes and manage files and URLs using their default application.

## Install

_This plugin requires a Rust version of at least **1.70**_

There are three general methods of installation that we can recommend.

1. Use crates.io and npm (easiest, and requires you to trust that our publishing pipeline worked)
2. Pull sources directly from Github using git tags / revision hashes (most secure)
3. Git submodule install this repo in your tauri project and then use file protocol to ingest the source (most secure, but inconvenient to use)

Install the Core plugin by adding the following to your `Cargo.toml` file:

`src-tauri/Cargo.toml`

```toml
[dependencies]
tauri-plugin-shell = "2.0.0-alpha"
# alternatively with Git:
tauri-plugin-shell = { git = "https://github.com/tauri-apps/plugins-workspace", branch = "v2" }
```

You can install the JavaScript Guest bindings using your preferred JavaScript package manager:

> Note: Since most JavaScript package managers are unable to install packages from git monorepos we provide read-only mirrors of each plugin. This makes installation option 2 more ergonomic to use.

```sh
pnpm add @tauri-apps/plugin-shell
# or
npm add @tauri-apps/plugin-shell
# or
yarn add @tauri-apps/plugin-shell

# alternatively with Git:
pnpm add https://github.com/tauri-apps/tauri-plugin-shell#v2
# or
npm add https://github.com/tauri-apps/tauri-plugin-shell#v2
# or
yarn add https://github.com/tauri-apps/tauri-plugin-shell#v2
```

## Usage

First you need to register the core plugin with Tauri:

`src-tauri/src/main.rs`

```rust
fn main() {
    tauri::Builder::default()
        .plugin(tauri_plugin_shell::init())
        .run(tauri::generate_context!())
        .expect("error while running tauri application");
}
```

Afterwards all the plugin's APIs are available through the JavaScript guest bindings:

```javascript
import { Command } from "@tauri-apps/plugin-shell";
Command.create("git", ["commit", "-m", "the commit message"]);
```

## Contributing

PRs accepted. Please make sure to read the Contributing Guide before making a pull request.

## License

Code: (c) 2015 - Present - The Tauri Programme within The Commons Conservancy.

MIT or MIT/Apache 2.0 where applicable.
