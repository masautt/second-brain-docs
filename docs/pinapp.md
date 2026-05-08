# pinapp — Personal Information Application

pinapp is a structured contact book and relationship tracker — people, family trees, contact info, life events, and context tags. It's the "who" to finapp's "what."

## Goals

- Replace scattered contacts and mental models with a queryable people database
- Visualize family trees and social networks
- Track relationships across different areas of life (work, family, friends, networking)
- Your data, your database — not locked in any platform

## How it fits together

```mermaid
graph TD
    DB[(Supabase\npeople + property schemas)]
    PW[pinapp-web\nMFE host - planned]
    FT[pinapp-ftree-comp\nfamily tree & contacts]

    DB --> PW
    PW --> FT
```

---

## pinapp-web _(planned)_

The MFE host for pinapp components. Not yet built — `pinapp-ftree-comp` runs standalone today. Will mirror the pattern of `finapp-web` once built.

---

## pinapp-ftree-comp

Interactive family tree and contact viewer.

```mermaid
graph LR
    DB[(Supabase)] --> TB[tree-builder.ts]
    TB --> FTC[FamilyTreeCanvas\nXYFlow graph]
    TB --> CP[ContactsPage\npeople list]
    FTC --> PDP[PersonDetailPanel]
    PDP --> CON[Contacts]
    PDP --> DAT[Dates]
    PDP --> REL[Relationships]
```

**Features**:
- Canvas-based family tree — drag, zoom, pan
- Person detail panel — contacts, key dates, relationships
- Context tagging — see who belongs to which part of your life
- Full-text search and filter
- Auth guard (login required)
- Static data fallback for offline / demo mode

**Stack**: React 19, Vite (Module Federation), @xyflow/react, Supabase, Tailwind, Vitest

---

## Data Model

### People & relationships

```mermaid
erDiagram
    PEOPLE {
        string first_name
        string preferred_name
        string nickname
    }
    RELATIONSHIPS {
        string relationship_type
        date start_date
        date end_date
    }
    CONTACT_INFO {
        string type
        string value
    }
    PERSON_CONTEXTS {
        string context_type
    }
    PERSON_DATES {
        string date_type
        date date_value
    }

    PEOPLE ||--o{ RELATIONSHIPS : "has"
    PEOPLE ||--o{ CONTACT_INFO : "has"
    PEOPLE ||--o{ PERSON_CONTEXTS : "tagged with"
    PEOPLE ||--o{ PERSON_DATES : "has"
```

### Address history (property schema)

```mermaid
erDiagram
    PEOPLE ||--o{ PERSON_ADDRESSES : "lived at"
    PERSON_ADDRESSES }o--|| ADDRESSES : "points to"
    ADDRESSES {
        string street
        string city
        string state
    }
    ADDRESSES ||--o{ ADDRESS_ZESTIMATES : "has"
    ADDRESSES ||--o{ ADDRESS_TAX_HISTORY : "has"
    ADDRESSES ||--o{ ADDRESS_SCHOOLS : "near"
```

### Relationship types

`parent_of` · `sibling_of` · `friend_of` · `husband_of` · `wife_of` · `coworker_of` · `acquaintance_of` _(extensible)_

### Context types

| Context | What it means |
|---------|--------------|
| `family` | Blood relatives, in-laws |
| `work` | Coworkers, managers, reports |
| `friend` | Personal friends |
| `networking` | Professional contacts |
| `romantic` | Romantic history |
| `childhood` | People from early life |
| `other` | Everything else |

### Other tracked data

| Table | What |
|-------|------|
| `fun_facts` | Memorable things about a person |
| `cross_stitches` | Cross-stitch nametag tracking |
| `ethnicities` / `races` | Multiracial identity support |
| `person_date_types` | Birthday, death day, milestones |
| `contact_info_types` | Phone, email, LinkedIn, social |

---

## CLI Management

People data is managed via the `second-brain-scripts` CLI — add/update people, relationships, and contexts interactively. See [second-brain-scripts](./second-brain-scripts.md).
