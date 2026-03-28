# daily-motd-themes

Community themes and extensions for [daily-motd](https://github.com/mennoliefstingh/daily-motd).

## Built-in themes

These themes are bundled with `daily-motd` by default:

| Language | Theme | File |
|----------|-------|------|
| English | Today in Nature | `en/today-in-nature.yaml` |
| Dutch | Vandaag in de Natuur | `nl/today-in-nature.yaml` |

## Extensions

See [`extensions/`](extensions/) for command-based extensions that fetch live data (e.g. Wikipedia).

## Installing a theme

```sh
daily-motd install-source today-in-nature
```

Or manually copy a YAML file to `~/.config/daily-motd/sources/<language>/`.

## Contributing a theme

1. Fork this repository
2. Generate a scaffold: `daily-motd generate --name "My Theme" --output en/my-theme.yaml`
3. Fill in your messages
4. Open a pull request

Theme YAML format:

```yaml
name: My Theme

messages:
  01/01: Your message for January 1st.
  02/01: Your message for January 2nd.
  # ... 366 entries total (DD/MM), including 29/02 for leap years
```

## License

- **Today in Nature** data: [CC BY-NC-SA 3.0 NL](https://creativecommons.org/licenses/by-nc-sa/3.0/nl/) — © Marcus Coates
- **Repository structure, extensions, and other themes**: MIT
