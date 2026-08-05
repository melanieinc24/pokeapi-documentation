# Pokémon Endpoint

## Overview

The Pokémon endpoint gives you detailed information about any Pokémon, 
including its stats, abilities, moves, and more.

## Get a Specific Pokémon

### Request

GET /pokemon/{id or name}

**Base URL:** https://pokeapi.co/api/v2/

**Examples:**
- `https://pokeapi.co/api/v2/pokemon/1` (by ID)
- `https://pokeapi.co/api/v2/pokemon/bulbasaur` (by name)

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | Integer | Unique identifier for this Pokémon |
| `name` | String | The Pokémon's name |
| `height` | Integer | Height in decimeters |
| `weight` | Integer | Weight in hectograms |
| `base_experience` | Integer | XP earned when caught |
| `types` | Array | List of types this Pokémon has (e.g., Grass, Poison). Pokémon can have 1-2 types. |
| `abilities` | Array | A list of abilities this Pokémon can have. is_hidden tells if it's a special hidden ability. |
| `stats` | Array | The base_stat is the value. effort shows how much this stat contributes when leveling up. |
| `moves` | Array | All the moves and attacks this Pokémon can learn. |

### Example Response

**Request:**

GET https://pokeapi.co/api/v2/pokemon/1

**Response:**
```json
{
  "id": 1,
  "name": "bulbasaur",
  "height": 7,
  "weight": 69,
  "base_experience": 64,
  "types": [
    {
      "type": {
        "name": "grass"
      }
    }
  ]
}
```

**What's in this response:**

This shows Bulbasaur's core information. Notice that `types` is an array 
(not a simple string) — this is because Pokémon can have multiple types. 
The `base_experience` tells you how much XP a trainer gets when catching it. 

The full response also includes `abilities`, `moves`, and `stats` arrays 
with more detailed information if you need it.


## Common Use Cases

### Get a Pokémon's Type for Battle Matchups
You're building a battle simulator. You need to know if Fire is strong against Grass.

```
GET /pokemon/charmander
```

Look at the `types` field to determine type advantages.

### Find What Moves a Pokémon Can Learn

You're building a team builder app. You want to show what attacks each Pokémon can use.

Check the moves array to see all available attacks.
```
GET /pokemon/pikachu
```

### Compare Pokémon Stats
You want to know which Pokémon is stronger (higher attack, defense, etc.).

```
GET /pokemon/1
GET /pokemon/4
```

### Find Hidden Abilities
You're building a competitive team builder and want to show rare hidden abilities.

```
GET /pokemon/bulbasaur
```

Check the `abilities` array and look for `is_hidden: true`.

### Find Past Stats and Past Types
You want to see how a Pokémon's stats changed in earlier game versions.

```
GET /pokemon/bulbasaur
```

Check the `past_abilities` array and `past_types` array.

## Tips


### Use ID or Name — Both Work

```
GET /pokemon/1 ← By ID (faster)
GET /pokemon/pikachu ← By name (more readable)
```

Both return the same data. Use whichever is convenient.

### IDs Are Faster Than Names
If performance matters, use IDs instead of names. IDs are simpler for the server to look up.

### The Response Can Be Large
The full response includes hundreds of moves and abilities. If you only need specific fields, consider filtering on your end instead of requesting everything.

### Use the URLs in the Response
The response includes URLs to related data (types, abilities, moves). Use these to get more details without guessing endpoints.

### Cache Results When Possible
Pokémon data doesn't change often. Store results locally to reduce API calls.
