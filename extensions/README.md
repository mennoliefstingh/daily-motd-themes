# Extensions

Extensions are command-based dynamic sources for `daily-motd`. Instead of a static list of messages, an extension runs a shell command each time `daily-motd` is invoked and displays the output.

## Installing an extension

Copy a YAML file from this directory to `~/.config/daily-motd/extensions/`:

```sh
cp wikipedia-on-this-day.yaml ~/.config/daily-motd/extensions/
```

Then select it by name:

```sh
daily-motd --source "Wikipedia On This Day"
```

## Extension YAML format

```yaml
name: My Extension        # Display name (used with --source)
type: command             # Must be "command"
command: |                # Shell command to run; output becomes the MOTD
  echo "Hello, world!"
cache: eod                # How long to cache the output (see below)
timeout: 10s              # Max time to wait for the command
fallback: "Fallback text" # Shown if the command fails or times out
```

## Template variables

The following placeholders are replaced before the command is executed:

| Variable   | Example | Description           |
|------------|---------|-----------------------|
| `{{day}}`  | `7`     | Day of month (no leading zero) |
| `{{month}}`| `3`     | Month number (no leading zero) |
| `{{year}}` | `2026`  | Four-digit year       |
| `{{dd/mm}}`| `07/03` | Zero-padded DD/MM     |
| `{{mm/dd}}`| `03/07` | Zero-padded MM/DD     |

## Cache TTL options

| Value  | Description              |
|--------|--------------------------|
| `eod`  | End of day               |
| `eoh`  | End of hour              |
| `eow`  | End of week              |
| `eom`  | End of month             |
| `24h`  | 24 hours from last fetch |
| `7d`   | 7 days from last fetch   |
| `none` | Never cache; run every time |

## Wikipedia On This Day

**Requirements:** `curl` and `jq` must be installed.

```sh
# macOS
brew install jq

# Debian/Ubuntu
sudo apt install jq curl
```

**Usage:**

```sh
daily-motd --source "Wikipedia On This Day"
```
