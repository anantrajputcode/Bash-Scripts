# Bash Scripts

A collection of small, focused Bash scripts built to automate everyday tasks — backups, cleanup, system checks, and other things I got tired of doing manually.

Each script lives in its own folder with a short description below and its own usage notes inside the script itself.

---

## Scripts

| Script | Description | Status |
|---|---|---|
| [`backup`](./backup) | Automates backing up recently modified files into a timestamped `.tar.gz`, with auto-cleanup of old backups | Working |

*(New scripts will be added here as they're built.)*

---

## Getting Started

Clone the repo:

```bash
git clone https://github.com/<your-username>/bash-scripts.git
cd bash-scripts
```

Make any script executable:

```bash
chmod +x <script-name>
```

Optionally, add this repo's scripts to your `$PATH` so you can run them from anywhere:

```bash
export PATH="$HOME/bash-scripts:$PATH"
```

Add that line to your `~/.zshrc` or `~/.bashrc` to make it permanent, then reload:

```bash
source ~/.zshrc
```

---

## Requirements

- Bash (v4+ recommended)
- Standard Unix utilities (`find`, `tar`, `mv`, etc. — noted per-script if anything extra is needed)

---

## Repo Structure

```
bash-scripts/
├── README.md          # This file
├── backup/
│   ├── backup          # The script itself
│   └── README.md        # Script-specific notes (optional)
└── ...more scripts as they're added
```

---

## License

This project is licensed under the MIT License — see the [LICENSE](./LICENSE) file for details.

---

## Author

**Anant Rajput**
Feel free to open an issue or PR if you spot a bug or have a suggestion.
