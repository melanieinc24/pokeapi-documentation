# Pokémon Endpoint

## Overview

The Pokémon endpoint retrieves information about a Pokémon, including its physical characteristics, types, abilities, stats, and moves.

Use this endpoint to retrieve Pokémon data by name or numeric ID.

## Get a Specific Pokémon

**HTTP method:** `GET`

**Endpoint:** `/pokemon/{id or name}`

**Base URL:** `https://pokeapi.co/api/v2/`

### Path Parameter

| Parameter | Type | Required | Description |
|---|---|---|---|
| `id or name` | Integer or String | Yes | The Pokémon's numeric ID or name. |

### Example Requests

Retrieve Bulbasaur by ID:

```bash
curl https://pokeapi.co/api/v2/pokemon/1
```

Retrieve Bulbasaur by name:

```bash
curl https://pokeapi.co/api/v2/pokemon/bulbasaur
```

Both requests retrieve the same Pokémon resource.

## Response Fields

The following table describes selected top-level fields returned by the endpoint.

| Field | Type | Description |
|---|---|---|
| `id` | Integer | Unique numeric identifier for the Pokémon. |
| `name` | String | Name of the Pokémon. |
| `height` | Integer | Height in decimeters. |
| `weight` | Integer | Weight in hectograms. |
| `base_experience` | Integer | Base experience yield for defeating the Pokémon. |
| `types` | Array | Pokémon types, such as Grass or Poison, with slot information. |
| `abilities` | Array | Available abilities, including whether an ability is hidden. |
| `stats` | Array | Base stats and effort values associated with the Pokémon. |
| `moves` | Array | Moves the Pokémon can learn, with associated version information. |

## Example Response

**Request:**

```http
GET https://pokeapi.co/api/v2/pokemon/1
```

**Response (abbreviated):**

```json
{
  "id": 1,
  "name": "bulbasaur",
  "height": 7,
  "weight": 69,
  "base_experience": 64,
  "types": [
    {
      "slot": 1,
      "type": {
        "name": "grass",
        "url": "https://pokeapi.co/api/v2/type/12/"
      }
    },
    {
      "slot": 2,
      "type": {
        "name": "poison",
        "url": "https://pokeapi.co/api/v2/type/4/"
      }
    }
  ]
}
```

This abbreviated response shows Bulbasaur's identifying information, physical characteristics, and types.

The `types` field contains an array of objects because a Pokémon can have more than one type. Each object identifies the type and provides a URL for retrieving additional type information.

The complete response includes additional fields, such as `abilities`, `moves`, and `stats`.

## Common Use Cases

### Identify Pokémon Types for Battle Matchups

When building a battle simulator, retrieve a Pokémon's types to identify which type matchups to evaluate.

```http
GET /pokemon/charmander
```

Inspect the `types` array to identify Charmander's type.

To determine strengths and weaknesses, retrieve the corresponding Type resource and inspect its damage relationships.

### Find Moves a Pokémon Can Learn

A team-building application might need to display available moves for a particular Pokémon.

```http
GET /pokemon/pikachu
```

Inspect the `moves` array to identify moves and associated version details.

### Compare Pokémon Stats

To compare two Pokémon, retrieve their data separately:

```http
GET /pokemon/1
GET /pokemon/4
```

Compare values in the `stats` arrays, such as attack, defense, and speed.

### Identify Hidden Abilities

To find a Pokémon's hidden abilities:

```http
GET /pokemon/bulbasaur
```

Inspect the `abilities` array. An ability with `is_hidden` set to `true` is classified as a hidden ability.

### Retrieve Historical Pokémon Data

Some Pokémon resources contain historical information about types or abilities.

```http
GET /pokemon/bulbasaur
```

Inspect fields such as `past_types` and `past_abilities`, where available, to identify changes associated with earlier game generations.

## Tips and Best Practices

### Use an ID or Name

Pokémon can be retrieved using either their numeric ID or name.

```http
GET /pokemon/1
GET /pokemon/bulbasaur
```

Choose the identifier that best fits your application's requirements.

### Handle Large Responses

Pokémon resources can contain extensive move and version information.

If your application only needs specific fields, extract the required values from the returned JSON.

### Follow Related Resource URLs

Response objects contain URLs to related resources, such as types, abilities, and moves.

Use these URLs to retrieve additional information.

### Cache Data When Appropriate

Pokémon data generally changes infrequently. Consider caching responses to reduce repeated requests and improve application performance.
