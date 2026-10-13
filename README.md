<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/wordmark-dark.svg"><img alt="stlabs" src="assets/wordmark-light.svg" width="240"></picture></p>

<p align="center">STLabs tickets in your terminal.</p>

<p align="center"><a href="https://github.com/Standard-Template-Labs/cli/releases/tag/v0.1.0"><img alt="Release v0.1.0" src="https://img.shields.io/badge/release-v0.1.0-DC5A1C?style=flat&labelColor=5A5C63"></a> <a href="https://github.com/Standard-Template-Labs/cli/releases"><img alt="macOS and Linux" src="https://img.shields.io/badge/platforms-macOS%20%7C%20Linux-2F6FED?style=flat&labelColor=5A5C63"></a> <a href="https://stlabs.com/terms"><img alt="License" src="https://img.shields.io/badge/license-STLabs%20terms-C24E17?style=flat&labelColor=5A5C63"></a></p>

<p align="center"><img alt="stlabs listing tickets in a terminal" src="assets/cover.svg" width="720"></p>

## About

stlabs brings STLabs tickets to your terminal.

- Read, search, create and update tickets without leaving the shell.
- Script it: JSON out, exit codes, safe retries with an idempotency key.
- One file per platform, no runtime to install.
- Built from the same API description as the service, so it never drifts.

## Installation

stlabs is available for macOS (Apple silicon) and Linux (x86_64).

### macOS

```sh
curl -fsSL -o stlabs https://github.com/Standard-Template-Labs/cli/releases/latest/download/stlabs-darwin-arm64
chmod +x stlabs && sudo mv stlabs /usr/local/bin/
```

### Linux

```sh
curl -fsSL -o stlabs https://github.com/Standard-Template-Labs/cli/releases/latest/download/stlabs-linux-x86_64
chmod +x stlabs && sudo mv stlabs /usr/local/bin/
```

Check the install with `stlabs --version`.

macOS may block the first run of an unsigned app. If it does, open System Settings, Privacy & Security, and choose Open Anyway.

### Update and uninstall

Update: download the new release over the old file with the install lines above.

Uninstall: run `stlabs logout`, then remove `/usr/local/bin/stlabs` and `~/.config/stlabs`.

## Usage

**List and read.** On a terminal a list is a table; everything else is JSON.

```sh
stlabs tickets list --limit 3              # the newest tickets, as a table on a terminal
stlabs tickets get TKT-DUSK-MERIDIAN-1615  # one ticket, as JSON
```

```
┌─────────────────────────┬───────┬───────────────────────────────┐
│ id                      │ state │ title                         │
├─────────────────────────┼───────┼───────────────────────────────┤
│ TKT-DUSK-MERIDIAN-1615  │ open  │ New starter needs a laptop    │
│ TKT-SABLE-ECHO-5512     │ open  │ VPN drops every hour          │
│ TKT-KESTREL-BEACON-6866 │ open  │ Printer on floor 3 is offline │
└─────────────────────────┴───────┴───────────────────────────────┘
```

<details>
<summary>Example output of <code>tickets get</code></summary>

```json
{
  "id": "TKT-DUSK-MERIDIAN-1615",
  "title": "New starter needs a laptop",
  "state": "open",
  "priority": "normal",
  "queue": "2c076030-eb94-51a1-8325-40b0c777ad23",
  "requester": {
    "id": "6a1f0c1e-3b1d-5c8e-9f0a-000000000001",
    "display_name": "Dana Okafor"
  },
  "assignee": null,
  "created_at": "2026-09-14T09:00:38Z",
  "updated_at": "2026-09-14T09:00:38Z",
  "service_level": {
    "response_due_at": null,
    "resolution_due_at": null,
    "resolution_paused": false,
    "breach_count": 0
  },
  "available_actions": {
    "transitions": [
      "in_progress",
      "on_hold",
      "resolved",
      "closed",
      "canceled"
    ],
    "editable_fields": [
      "title",
      "description",
      "priority",
      "assignee_id",
      "queue"
    ]
  },
  "description": "Reported from the terminal.",
  "routing": "settled",
  "synced_from": null
}
```

</details>

**Create and update.** Fields go in one argument of `name: value` pairs.

```sh
stlabs tickets create 'title: Printer on floor 3 is offline, requester_email: dana@northwind.example'  # file a ticket
stlabs tickets update TKT-DUSK-MERIDIAN-1615 'priority: urgent'                                        # change its fields
stlabs tickets comments create TKT-DUSK-MERIDIAN-1615 'body: Replaced the toner.'                      # add a comment
```

**Script it.** Piped or redirected output is JSON, one record per command, so pipe it into jq or capture it. A command that fails exits with a code that says why.

```sh
stlabs tickets get TKT-DUSK-MERIDIAN-1615 | jq -r .state  # piped output is JSON
```

While access is not open, sign-in and every API call print the access notice and exit with code 10.

## Documentation

- [Documentation](https://standard-template-labs.github.io/cli/): the command line guide and the API reference.
- [Releases](https://github.com/Standard-Template-Labs/cli/releases): every build, with checksums and notices.

## Questions and support

Questions, access requests and problems: support@stlabs.com.

Security issues: security@stlabs.com, see https://stlabs.com/security.

## License

The stlabs binary is STLabs software, under the terms at https://stlabs.com/terms. The open source software bundled in it is listed, with its licenses, in THIRD_PARTY_NOTICES.md on each release.
