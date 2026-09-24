# Fear & Greed for Gloom

The CNN Fear & Greed sentiment gauge, its history, and the seven indicators behind it: market momentum, stock price strength, stock price breadth, put and call options, junk bond demand, market volatility, and safe haven demand.

## Install

Requires Gloom 0.15.0 or newer. Gloom restores this plugin once for existing installations when it moves out of the core app: saved panes keep working because the pane and template ids are unchanged, a previously disabled plugin stays disabled, and a deliberate removal is respected.

```sh
gloomberb install gloom-sh/gloom-fear-greed
```

Open `FNG` in the command bar. Also in the hosted web app at term.gloom.sh, where the host proxies the data source.

## Usage

The readings at the previous close and one week, month, and year ago sit in a band along the top, above today's gauge, a year of index history, and the seven indicator charts. `r` refreshes. `gloomberb fear-greed` prints the same data on the command line, and `gloomberb fn fear-greed` returns the headless model.

## Data

CNN's public Fear & Greed endpoint at `production.dataviz.cnn.io`. Unofficial; if CNN changes it the pane breaks until this plugin is updated, which is one reason it is a plugin rather than part of the core app. The last good reading is cached so the pane has something to show before the first fetch.

## Development

```sh
bun install
# Link a Gloom checkout, as the plugin installer does:
ln -s /path/to/gloomberb node_modules/gloomberb
ln -s /path/to/gloomberb/node_modules/react node_modules/react
bun run typecheck
bun test
```

`gloomberb` and `react` are peer dependencies, never real ones. Gloom symlinks its own copies into every plugin directory on install and on load, so there is exactly one instance of each in the process. CI links the host the same way.

## License

MIT
