# HAR Debugger Skill

Analyze a `.har` file with a bug description to find slow/failed requests and explain likely causes using HAR evidence only.

## Inputs
- `har_file`: Path to a `.har` file on disk.
- `bug_description`: Concise description of the bug symptoms.
- `start_time`: (optional) ISO timestamp or epoch ms for when the bug started.
- `end_time`: (optional) ISO timestamp or epoch ms for when the bug ended.
- `socket_map`: (optional) Inline list of socket-to-API mappings in the form `<socket-name>: <api-name>` to override defaults.

## Default socket map
The skill automatically loads mappings from:
- `/Users/hynguyen/.codex/skills/har-debugger/references/socket_map.md`

Format (one per line):
```
<socket-name>: <api-name>
```

## Example usage
Use `$har-debugger` on `/absolute/path/to/session.har`. The app hangs when clicking Save between `2026-02-10T10:20:00Z` and `2026-02-10T10:22:00Z`. Identify slow/failed requests and summarize the likely cause with evidence.

## Output
- Root-cause summary with confidence notes
- Relevant requests (method, URL, status, time, response received time, response header time, evidence)
- Evidence tied to the bug description
- Debugging recommendations

## Constraints
- Do not fabricate data not in the HAR.
- Keep hypotheses grounded in observed requests and timings.
