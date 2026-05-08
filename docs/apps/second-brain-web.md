# second-brain-web

The shell application that composes second brain apps into one interface.

## Responsibilities

- Top-level routing between app domains
- Shared Supabase auth lifecycle
- Shared shell UI (navigation/sidebar)
- Runtime loading of remote apps via Module Federation

## Planned Route Structure

| Route | App |
|-------|-----|
| `sbrain.example.com/` | Dashboard / home |
| `sbrain.example.com/finance` | finapp-web |
| `sbrain.example.com/people` | pinapp-web |
| `sbrain.example.com/misc` | minapp-web (future) |

## Status

Shell is in progress. `finapp-web` currently acts as the effective entry point while the unified shell is being built.

## Related Docs

- [Architecture Overview](../architecture/overview.md)
- [Micro-Frontend Composition](../architecture/mfe.md)
- [Repo README](../../second-brain/README.md)
