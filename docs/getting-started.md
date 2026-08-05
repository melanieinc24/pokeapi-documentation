# Getting Started with PokéAPI

## What is PokéAPI?

PokéAPI is a free, open-source RESTful API providing comprehensive Pokémon data including:
- Pokémon species information
- Moves/attacks
- Items
- Abilities
- Types
- Encounters
- And much more!


## Why Use PokéAPI?

- **Build Pokémon projects fast** — Don't spend time collecting data; focus on building
- **No authentication hassle** — Start immediately, no API keys or signup
- **Comprehensive data** — Every Pokémon, move, type, item, and more
- **Perfect for learning** — Great first API to practice with
- **Free to use** — No cost, no limits to worry about

## API Base URL

All requests start with:
https://pokeapi.co/api/v2/

## What You Need to Know
- Do you need an API key? (In PokéAPI's case: NO) 
- Do you need to sign up? (PokéAPI: NO) 
- Any rate limits to know about? (PokéAPI: Be respectful)

## No Setup Required

Unlike many APIs, **PokéAPI requires no authentication or API keys**. You can start using it immediately.

Most APIs require:
- Signing up for an account
- Getting an API key
- Configuring authentication

PokéAPI skips all that. Just make a request. It works immediately.

## Your First Request

Get Pokémon #1 (Bulbasaur):

```bash
curl https://pokeapi.co/api/v2/pokemon/1
```
Or paste this in your browser:
```
https://pokeapi.co/api/v2/pokemon/1
```
## Response

You'll get back JSON data about Bulbasaur including:
- Its ID, name, height, weight
- What type it is (Grass/Poison)
- What abilities it has
- All its stats

## Next Steps

- Try getting a different Pokémon: /pokemon/25 (Pikachu)
- Try getting by name: /pokemon/pikachu
- Read Pokémon Endpoint for detailed field explanations
- Try Type Endpoint to filter by type
