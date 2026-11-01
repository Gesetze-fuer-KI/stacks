# stacks

How [gesetze-fuer-ki.de](https://gesetze-fuer-ki.de) runs [gesetze-fuer-ki](https://github.com/Gesetze-fuer-KI/gesetze-fuer-ki) in production: the compose file of the server, one folder per service. Public as a worked example.

| Folder | What runs | Reachable |
|---|---|---|
| `gesetze-fuer-ki/` | The MCP server for German federal and state law, and its documentation site; `data/` is its clone of the law texts and its search index, rebuilt when deleted (about a minute) | On the server's private address only: the server's Caddy passes requests on |

## How it is used

The server checks this repository out at `/srv/stacks/gesetze-fuer-ki/`. A private Ansible repository writes the `.env` and runs `docker compose up`.

- **No secrets and no server addresses in here.** `.env.example` lists the names; the values are written on the server.
- **Nobody edits files on the server.** A change is a commit here, then a deployment.
- **Versions are pinned.** Dependabot opens a pull request when a new image exists; merging it is the decision to upgrade.

The history before 2026-11-01 comes from [notefeed/stacks](https://github.com/notefeed/stacks), where this folder started.
