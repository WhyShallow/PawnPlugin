# Pawn

Advanced Minecraft Chess for Paper 26.1.2.

## Features

- Complete server-authoritative chess engine
- Legal move validation, castling, en passant and all four promotions
- Check, checkmate, stalemate, threefold repetition, fifty-move rule and insufficient material
- Configurable chess clocks with increments
- Player challenges and configurable time controls
- Rated and casual games with Elo-style ratings
- Player statistics, leaderboard and persisted game history
- PGN and FEN support
- Spectator mode
- Matchmaking queue foundation
- Tournament foundation (single-elimination-ready model)
- Physical Minecraft chess boards
- Adventure-based messages and inventories
- SQLite persistence with asynchronous database writes
- Optional reflection-based ViaVersion integration; no ViaVersion/ViaBackwards classes are bundled or required
- GitHub Actions CI

## Requirements

- Paper 26.1.2
- Java 25
- Maven 3.9+

For cross-version client support, install the server-side ViaVersion and ViaBackwards plugins separately.

## Installation

1. Build with `mvn clean package`.
2. Put `target/Pawn-1.0.0.jar` into the Paper `plugins/` directory.
3. Start the server.
4. Create a board with `/chessadmin createboard main`.

## Commands

### Players

`/chess`
`/chess challenge <player> [time] [color] [rated|casual]`
`/chess accept <player>`
`/chess deny <player>`
`/chess resign`
`/chess draw`
`/chess draw accept`
`/chess draw deny`
`/chess spectate <player>`
`/chess leave`
`/chess stats [player]`
`/chess leaderboard`
`/chess history`
`/chess game <id>`
`/chess queue`
`/chess queue leave`
`/chess tournament <create|join|leave|start|info>`

### Admin

`/chessadmin reload`
`/chessadmin createboard <name>`
`/chessadmin deleteboard <name>`
`/chessadmin listboards`
`/chessadmin debug`
`/chessadmin forceend [gameId]`

## Data

Pawn stores player ratings, statistics and finished games in SQLite. Board locations remain in `boards.yml` so they can be edited or backed up independently.

## ViaVersion / ViaBackwards

Pawn does not declare compile-time dependencies on ViaVersion or ViaBackwards in the initial Maven project because exact dependency versions are intentionally left for the server maintainer. The integration uses reflection and is isolated in `hook/`.

## Development

```text
src/main/java/dev/whyshallow/pawn/
  board/
  chess/
  command/
  config/
  database/
  game/
  gui/
  hook/
  listener/
  matchmaking/
  player/
  rating/
  spectator/
  tournament/
  utility/
```

Run:

```bash
mvn clean test package
```

The shaded SQLite driver is included. Paper is `provided`.

## Policy note

Pawn does not implement player-to-player betting, wagering, gambling, or currency/item staking. Server administrators may configure ordinary rewards for achievements or competitive progression.
