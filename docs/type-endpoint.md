# Type Endpoint

**Status: Work in Progress**

## Overview

The Type endpoint provides information about a specific Pokémon type, including damage relationships, Pokémon associated with that type, and moves that use it.

## Get a Specific Type

**HTTP method:** `GET`

**Endpoint:** `/type/{id or name}`

**Base URL:** `https://pokeapi.co/api/v2/`

### Example Requests

```http
GET https://pokeapi.co/api/v2/type/fire
GET https://pokeapi.co/api/v2/type/water
GET https://pokeapi.co/api/v2/type/grass
```

### Selected Response Fields

| Field | Type | Description |
|---|---|---|
| `id` | Integer | Unique identifier for the type. |
| `name` | String | Name of the type, such as `fire` or `water`. |
| `damage_relations` | Object | Damage multipliers associated with attacking and defending against other types. |
| `pokemon` | Array | Pokémon associated with this type. |
| `moves` | Array | Moves associated with this type. |

## Planned Documentation

The following sections are still being developed:

- Example JSON response
- Interpreting damage relationships
- Finding Pokémon associated with a type
- Practical use cases and examples

For the complete API schema, see the [official PokéAPI documentation](https://pokeapi.co/docs/v2#types).
