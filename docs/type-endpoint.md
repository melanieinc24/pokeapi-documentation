# Type Endpoint

## Overview

The type endpoint provides information about a specific Pokémon type, 
including type matchups (what it's strong and weak against), all Pokémon 
with that type, and moves that use that type.

## Get a Specific Type

### Request
```
GET /type/{name}
```

**Base URL:** `https://pokeapi.co/api/v2/`

**Examples:** 

- `https://pokeapi.co/api/v2/type/fire`
- `https://pokeapi.co/api/v2/type/water`
- `https://pokeapi.co/api/v2/type/grass`


### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | Integer | Unique identifier for this type |
| `name` | String | The name of the type (e.g., "fire", "water") |
| `damage_relations` | Object | Shows what types are strong/weak against this type |
| `pokemon` | Array | List of all Pokémon with this type |
| `moves` | Array | List of all moves that use this type |

### Example Response

**Request:**

GET https://pokeapi.co/api/v2/type/fire

**Response:**




## Common Use Cases

"I'm building a battle game and need to know if Fire beats Grass"
"I'm building a Pokédex and want to show all Fire-type Pokémon"

## Tips
