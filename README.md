# Bitasmbl-Simple-Real-Time-Casino-Game-System-00e805-b9bbb1a779c7

## Description
A minimal real-time casino platform where authenticated players manage wallets, create and join game tables, and play a simple game. Services communicate via ASP.NET Core and SignalR; players interact through a React frontend. Lobby manages tables, enforces rules, and handles payouts by calling the Wallet service.

## Tech Stack
- ASP.NET Core
- Docker
- SQL
- React
- SignalR

## Requirements
- Implement Lobby payout logic so that after receiving the winner from Game1, 95% of the prize pool is credited to the winner via Wallet and 5% remains as margin.
- Validate dynamic rules from games.json when creating a game table (e.g., delayTime within allowed range).
- Use SignalR exclusively for player-driven actions (create/join/approve/cancel and in-game events) without HTTP polling.
- Protect wallet endpoints so only Lobby can perform debit/credit/rollback operations.
- Show real-time lobby updates in the React UI when tables are created, joined, approved, or canceled.

## Installation
bash
git clone https://github.com/he1snber8/Bitasmbl-Simple-Real-Time-Casino-Game-System-00e805-b9bbb1a779c7.git
cd Bitasmbl-Simple-Real-Time-Casino-Game-System-00e805-b9bbb1a779c7
docker compose up --build


## Usage
- Access React UI in browser after containers are running.
- Connect as player, manage wallet via flows exposed by Lobby, then create or join tables.

## Implementation Steps
1. Define games.json and model validation for table creation in ASP.NET Core Lobby service.
2. Implement SignalR hubs for Lobby and Game1 to handle create/join/approve/cancel and in-game events.
3. Add payout logic: Lobby computes prize pool, credits 95% to winner via Wallet, retains 5%.
4. Secure Wallet service so only Lobby can invoke debit/credit/rollback operations.
5. Build React components that subscribe to SignalR lobby hub for real-time table updates.
6. Wire React actions to SignalR calls instead of HTTP polling.
7. Persist tables, wallets, and game state in SQL via ASP.NET Core services.

## API Endpoints
- Lobby SignalR hub: player-driven actions and game events.
- Wallet service: debit, credit, rollback (restricted to Lobby).