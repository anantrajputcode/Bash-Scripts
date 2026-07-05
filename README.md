# Bash Scripts

A collection of small, focused Bash scripts built to automate everyday tasks — backups, file organization, connectivity checks, user provisioning, and other things I got tired of doing manually.

Each script lives in its own folder with a short description below and its own usage notes inside a dedicated README.

---

## Scripts

| Script | Description | Status |
|---|---|---|
| [`backup`](./backup) | Automates backing up recently modified files into a timestamped `.tar.gz`, with auto-cleanup of old backups | Working |
| [`filesorg`](./filesorg) | Sorts files in a directory into subfolders based on their file extension | Working |
| [`site-check`](./site-check) | Checks whether a given website or host is reachable via a single ping and reports the connection status | Working |
| [`user_make`](./user_make) | Creates a new local user account with a randomly generated password and forces it to expire on first login | Working |

*(New scripts will be added here as they're built.)*

---

## Getting Started

**1. Clone the repo**
```bash
git clone https://github.com/<your-username>/bash-scripts.git
cd bash-scripts
```

**2. Make a script executable**
```bash
chmod +x <script-name>/<script-name>
```

**3. (Optional) Add scripts to your `$PATH`**

This lets you run any script from anywhere, without `./` or a full path.
```bash
export PATH="$HOME/bash-scripts:$PATH"
```
Add that line to your `~/.zshrc` or `~/.bashrc` to make it permanent, then reload your shell:
```bash
source ~/.zshrc
```

---

## Requirements

- Bash (v4+ recommended)
- Standard Unix utilities — `find`, `tar`, `mv`, `ping`, `date`, `useradd`, `chpasswd`, `passwd`, etc.
- Some scripts (like `user_make`) require root/sudo privileges to run
- Anything script-specific is called out in that script's own README

---

## Repo Structure

```
bash-scripts/
├── README.md              # This file
├── backup/
│   ├── backup              # The script itself
│   └── README.md           # Script-specific notes
├── filesorg/
│   ├── filesorg             # The script itself
│   └── README.md           # Script-specific notes
├── site-check/
│   ├── site-check           # The script itself
│   └── README.md           # Script-specific notes
├── user_make/
│   ├── user_make            # The script itself
│   └── README.md           # Script-specific notes
└── ...more scripts as they're added
```

---

## Contributing

This is primarily a personal collection, but suggestions and fixes are welcome. Feel free to open an issue or PR if you spot a bug, see a better way to do something, or want to suggest a new script.

---

## License

This project is licensed under the MIT License — see the [LICENSE](./LICENSE) file for details.

---

## Author

**Anant Rajput**
