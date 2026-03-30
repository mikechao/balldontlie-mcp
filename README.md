# Balldontlie MCP Server

[![smithery badge](https://smithery.ai/badge/@mikechao/balldontlie-mcp)](https://smithery.ai/server/@mikechao/balldontlie-mcp)

[![Verified on MseeP](https://mseep.ai/badge.svg)](https://mseep.ai/app/07e29bcd-3fb7-46e6-b4b9-8908b3ef18f2)

[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/mikechao-balldontlie-mcp-badge.png)](https://mseep.ai/app/mikechao-balldontlie-mcp)

<a href="https://glama.ai/mcp/servers/@mikechao/balldontlie-mcp">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@mikechao/balldontlie-mcp/badge" alt="balldontlie-mcp MCP server" />
</a>

An MCP Server implementation that integrates the [Balldontlie API](https://www.balldontlie.io/), to provide information about players, teams and games for the NBA, NFL and MLB.

## Tools

- **get_teams**

  - Gets the list of team from one of the following leagues NBA (National Basketball Association), MLB (Major League Baseball), NFL (National Football League)
  - Inputs:
    - `league` (enum ['NBA', 'NFL', 'MLB']): The sports league to get teams for

- **get_players**

  - Gets the list of players from one of the following leagues NBA (National Basketball Association), MLB (Major League Baseball), NFL (National Football League)
  - Inputs:
    - `league` (enum ['NBA', 'NFL', 'MLB']): The sports league to get players for
    - `firstName` (string, optional): The first name of the player to search for
    - `lastName` (string, optional): The last name of the player to search for
    - `cursor` (number, optional): Cursor for pagination

- **get_games**

  - Gets the list of games from one of the following leagues NBA (National Basketball Association), MLB (Major League Baseball), NFL (National Football League)
  - Inputs:
    - `league` (enum ['NBA', 'NFL', 'MLB']): The sports league to get games for
    - `dates` (string[], optional): Get games for specific dates, format: YYYY-MM-DD
    - `teamIds` (string[], optional): Get games for specific games
    - `cursor` (number, optional): Cursor for pagination

- **get_game**

  - Get a specific game from one of the following leagues NBA (National Basketball Association), MLB (Major League Baseball), NFL (National Football League)
  - Inputs:
    - `league` (enum ['NBA', 'NFL', 'MLB']): The sports league to get the game for
    - `gameId` (number): The id of the game from the get_games tool

## Prompts

- **schedule_generator**

Given a league (NBA, MLB, NFL), a starting date and ending date generates an interactive schedule in Claude Desktop.

![claude desktop example](https://mikechao.github.io/images/schedule_geneartor_prompt.webp)

## Sample queries

With this MCP Server installed you can ask Claude or other LLM questions like the following.

```
Show me today's baseball games.
Can you find football players with the last name Purdy?
How many NBA players have the last name Ming?
```

## Configuration

### Getting an API Key

1. Sign up for account at [Balldontlie.io](https://www.balldontlie.io/)
2. The free plan is enough for this MCP Server

### Installing using Desktop Extension (DXT)

1. Download the `dxt` file from the [Releases](https://github.com/mikechao/balldontlie-mcp/releases)
2. Open it with Claude Desktop
   or
   Go to File -> Settings -> Extensions and drag the .DXT file to the window to install it

### Installing via Smithery

To install balldontlie-mcp for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@mikechao/balldontlie-mcp):

```bash
npx -y @smithery/cli install @mikechao/balldontlie-mcp --client claude
```

### Usage with Claude Desktop

Add this to your `claude_desktop_config.json`:

```json
{
  "mcp-servers": {
    "balldontlie": {
      "command": "npx",
      "args": [
        "-y",
        "balldontlie-mcp"
      ],
      "env": {
        "BALLDONTLIE_API_KEY": "YOUR API KEY HERE"
      }
    }
  }
}
```

### Usage with LibreChat

```yaml
mcpServers:
  balldontlie:
    command: sh
    args:
      - -c
      - BALLDONTLIE_API_KEY=your-api-key-here npx -y balldontlie-mcp
```

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License. For more details, please see the LICENSE file in the project repository.

## Disclaimer

This library is not officially associated with balldontlie.io. It is a third-party implementation of the balldontlie api with a MCP Server.

## Hosted deployment

A hosted deployment is available on [Fronteir AI](https://fronteir.ai/mcp/mikechao-balldontlie-mcp).

