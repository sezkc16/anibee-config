# anibee-config

Remote provider config for **AniBee** (personal iOS anime app).

The app fetches `providers.json` from here on launch
(`https://raw.githubusercontent.com/sezkc16/anibee-config/main/providers.json`)
and uses it for resolving streams. A bundled copy ships inside the app as
fallback when offline or the fetch fails.

**One JSON fix updates every install:** if a site's domain or endpoint
changes, edit `providers.json` here — every AniBee install picks it up on
next launch, no app update needed. Big changes (full redesign, stricter
Cloudflare) still need an app update.

## Format

- `version` — bump on every change (the app shows it in Settings > About).
- `providers[]` — each provider: `id`, `name`, `enabled`, `preferred`,
  `mirrors` (tried in order, rotates on failure), `endpoints` (URL
  templates with `{q}`, `{id}`, `{slug}`, `{episode}`, `{startAt}`
  placeholders), `note`.
