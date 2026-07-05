# user_make

A Bash script that automates creating a new local user account with a randomly generated password, forcing the password to expire on first login.

## Overview

This script was built to remove the manual effort of running `useradd` and `passwd` separately every time a new account needs to be provisioned. It handles account creation, password generation, and password expiry in a single step, making it suitable for quick provisioning of new users on a server.

## What It Does

1. Verifies the script is being run as root (via `sudo`)
2. Verifies a username was provided as an argument
3. Creates the user account with an optional comment (GECOS field)
4. Generates a random password based on the current timestamp
5. Sets the generated password for the new account
6. Forces the password to expire, requiring the user to set a new one on first login
7. Prints the username, password, and hostname for handoff

## Usage

```bash
sudo ./user_make USERNAME [COMMENT]
```

### Example

```bash
sudo ./user_make anant "Anant Rajput"
```

## Configuration

| Argument | Description | Required |
|---|---|---|
| `USERNAME` | Name of the account to create | Yes |
| `COMMENT` | Text for the GECOS/comment field (e.g. full name) | No |

## Output

```
Username: anant

Password: 1751234567891234567

Hostname: ip-172-11-x-xxx
```

The generated password should be shared with the user securely and changed immediately, since it's derived from a timestamp and isn't meant for long-term use.

## Requirements

- Bash
- Must be run with `sudo` or as `root`
- Standard Unix utilities: `useradd`, `chpasswd`, `passwd`, `date`, `hostname`

## Notes

- The account is created without a home directory (`-M`). Remove this flag if a home directory is required.
- The password is set using `chpasswd` for compatibility with Debian/Ubuntu systems (`passwd --stdin` is not available there).
- `passwd -e` immediately expires the password, so the new user must choose their own on first login.

## Example

```bash
$ sudo ./user_make anant
```

```
Username: anant

Password: 1751702345123456789

Hostname: ip-172-31-2-248
```

## License

This script is part of the [bash-scripts](../) collection and is licensed under the MIT License.
