# Getting Started with PokéAPI

## Overview

PokéAPI is a free, public REST API that provides Pokémon-related data, including species, abilities, moves, types, items, and encounters.

This guide shows you how to make your first API request and retrieve information about a Pokémon.

By the end of this guide, you'll know how to:

- Make a GET request to PokéAPI.
- Retrieve a Pokémon by its numeric ID or name.
- Identify key fields in the JSON response.

## Prerequisites

You need:

- An internet connection.
- A web browser or a terminal with curl installed.

PokéAPI does not require an account, API key, or authentication.

## Base URL

All API requests use the following base URL:

```text
https://pokeapi.co/api/v2/
```

Append a resource path to the base URL to request specific data.

For example, `/pokemon/1` retrieves information about Bulbasaur.

## Step 1: Make Your First API Request

Open a terminal and run the following command:

```bash
curl https://pokeapi.co/api/v2/pokemon/1
```

This command sends an HTTP GET request to the Pokémon endpoint.

Alternatively, paste the following URL into your browser:

```text
https://pokeapi.co/api/v2/pokemon/1
```

Both methods retrieve the Pokémon resource with the ID `1`.

## Step 2: Review the Response

If the request succeeds, PokéAPI returns an HTTP `200 OK` status and a JSON response containing information about Bulbasaur.

The following example shows selected fields from the response. Other fields have been omitted for readability.

```json
{
  "id": 1,
  "name": "bulbasaur",
  "height": 7,
  "weight": 69,
  "base_experience": 64
}
```

### Understanding the Response

| Field | Description |
|---|---|
| `id` | Unique numeric identifier for the Pokémon. |
| `name` | Name of the Pokémon. |
| `height` | Height in decimeters. |
| `weight` | Weight in hectograms. |
| `base_experience` | Base experience yield associated with defeating the Pokémon. |

The complete response includes additional information, such as types, abilities, stats, and moves.

## Step 3: Retrieve a Different Pokémon

You can retrieve Pokémon by numeric ID or name.

For example, to retrieve Pikachu by ID:

```bash
curl https://pokeapi.co/api/v2/pokemon/25
```

To retrieve Pikachu by name:

```bash
curl https://pokeapi.co/api/v2/pokemon/pikachu
```

Both requests return the Pokémon resource for Pikachu.

## Next Steps

Now that you've made your first API request, you can explore additional resources.

- [Pokémon Endpoint Reference](pokemon-endpoint.md) — Learn about available response fields and common use cases.
- [Type Endpoint Reference](type-endpoint.md) — Explore Pokémon types and their relationships. *Work in progress.*

You can also explore the [official PokéAPI documentation](https://pokeapi.co/docs/v2) for additional endpoints and resources.

## Best Practices

- **Use descriptive resource paths.** Request Pokémon by name when it makes your application logic easier to understand.
- **Handle unsuccessful requests.** Check HTTP status codes and account for missing resources.
- **Cache responses when appropriate.** Avoid repeatedly requesting data that rarely changes.
- **Use related resource URLs.** Follow URLs returned in API responses to retrieve additional information.
