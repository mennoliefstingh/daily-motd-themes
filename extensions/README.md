# Extensions

Extensions are command-based dynamic sources for `daily-motd`. Instead of a static list of messages, an extension runs a shell command each time `daily-motd` is invoked and displays the output.

## Installing an extension

Copy the YAML file to `~/.config/daily-motd/extensions/`:

```sh
# Example: Wikipedia On This Day
cp wikipedia-on-this-day/en.yaml ~/.config/daily-motd/extensions/wikipedia-on-this-day.yaml
```

Then select it by name:

```sh
daily-motd --source "Wikipedia On This Day"
```

## Available extensions

| Extension | Requires | Description |
|-----------|----------|-------------|
| [today-in-nature](today-in-nature/) | — | Daily nature fact (EN/NL) |
| [wikipedia-on-this-day](wikipedia-on-this-day/) | `curl`, `jq` | A selected Wikipedia event for today |
| [nasa-apod](nasa-apod/) | `curl`, `jq` | NASA Astronomy Picture of the Day |
| [github-trending](github-trending/) | `python3` | Top trending GitHub repos this week |
| [word-of-the-day](word-of-the-day/) | `curl`, `jq` | A curated word with its definition |
| [this-day-in-history](this-day-in-history/) | `curl`, `jq` | A historical event from today's date |
| [moon-phase](moon-phase/) | `python3` | Today's moon phase (no network needed) |

## Extension YAML format

```yaml
name: My Extension        # Display name (used with --source)
type: command             # Must be "command"
color: "#3366cc"          # Optional hex color for the box border
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
