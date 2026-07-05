# site-check

A Bash script that checks whether a given website or host is reachable by sending a single ICMP ping and reporting the connection status.

## Overview

This script was built as a quick, interactive way to verify connectivity to a site without remembering `ping` flags or parsing its output manually. It prompts for a target, performs a single ping test, and prints a clear success or failure message.

## What It Does

1. Prompts the user to enter a site or host to check
2. Sends a single ping (`-c 1`) to the target, suppressing raw ping output
3. Captures the exit status of the ping command
4. Waits 5 seconds before reporting the result
5. Prints a success message if the ping succeeded, or a failure message if it didn't

## Usage

```bash
site-check
```

If the script's directory has been added to your `$PATH`, it can be run from anywhere. Otherwise, run it directly:

```bash
./site-check
```

You'll be prompted to enter a site:

```
Which site you want to check: example.com
```

## Configuration

This script takes no configuration variables — the target site is supplied interactively at runtime via the `site` prompt.

## Output

The script prints one of the following to standard output:

```
successfully connected to site example.com
```

```
Unable to connect to the site.
```

## Requirements

- Bash
- Standard Unix utilities: `ping`, `read`, `sleep`

## Notes

- Only a single ping packet is sent, so results may vary on flaky or slow connections. Adjust the `-c 1` value in the script to send more packets for a more reliable check.
- The 5-second `sleep` is purely a pacing delay before the result is printed and does not affect the ping itself.
- Some hosts block ICMP ping requests entirely, which can produce a "Unable to connect" result even if the site is actually reachable (e.g. over HTTP/HTTPS).
- The script does not validate the input before pinging, so typos or empty input will simply result in a failed ping.

## Example

```bash
$ site-check
Which site you want to check: google.com
successfully connected to site google.com
```

```bash
$ site-check
Which site you want to check: not-a-real-site.tld
Unable to connect to the site.
```

## License

This script is part of the [bash-scripts](../) collection and is licensed under the MIT License.
