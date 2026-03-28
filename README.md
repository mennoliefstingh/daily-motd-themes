# daily-motd-themes

Community themes and extensions for [daily-motd](https://github.com/mennoliefstingh/daily-motd).

## Structure

```
extensions/
  today-in-nature/       # Built-in theme (also bundled with daily-motd)
    en.yaml
    nl.yaml
  wikipedia-on-this-day/
    en.yaml
  nasa-apod/
    en.yaml
  github-trending/
    en.yaml
  word-of-the-day/
    en.yaml
  this-day-in-history/
    en.yaml
  moon-phase/
    en.yaml
```

## Installing an extension

Copy the YAML file for the extension you want to `~/.config/daily-motd/extensions/`:

```sh
cp extensions/wikipedia-on-this-day/en.yaml ~/.config/daily-motd/extensions/wikipedia-on-this-day.yaml
```

Then use it:

```sh
daily-motd --source "Wikipedia On This Day"
```

## Available extensions

| Extension | Requires | Color |
|-----------|----------|-------|
| [Today in Nature](extensions/today-in-nature/) | — (embedded) | green |
| [Wikipedia On This Day](extensions/wikipedia-on-this-day/) | `curl`, `jq` | blue |
| [NASA APOD](extensions/nasa-apod/) | `curl`, `jq` | dark blue |
| [GitHub Trending](extensions/github-trending/) | `python3` | dark |
| [Word of the Day](extensions/word-of-the-day/) | `curl`, `jq` | purple |
| [This Day in History](extensions/this-day-in-history/) | `curl`, `jq` | brown |
| [Moon Phase](extensions/moon-phase/) | `python3` | indigo |

## Contributing a theme or extension

1. Fork this repository
2. Add your YAML file under `extensions/<your-extension-name>/en.yaml` (or `nl.yaml`, etc.)
3. Open a pull request

Theme YAML format:

```yaml
name: My Theme
color: "#e07b39"  # optional hex color for the border

messages:
  01/01: Your message for January 1st.
  02/01: Your message for January 2nd.
  # ... 366 entries total (DD/MM), including 29/02 for leap years
```

See [`extensions/README.md`](extensions/README.md) for the extension YAML format.

## License

- **Today in Nature** data: [CC BY-NC-SA 3.0 NL](https://creativecommons.org/licenses/by-nc-sa/3.0/nl/) — © Marcus Coates
- **Repository structure, extensions, and other themes**: MIT
