# 🐷 Greedy Pig Game Simulation Project

## 🌟 Overview
The Greedy Pig Game Simulation is a Python-based project that simulates the popular dice game, Greedy Pig. It's a simple dice game with very interesting and unpredictable dynamics when played by a large number of players. This primary school game's optimal play has been a subject of many academic papers and discussions. More information can be found here:

- [The Statistical Problem of Greedy Pigs](https://www.smh.com.au/education/the-statistical-problem-of-greedy-pigs-20140728-3cpk8.html)
- [Optimal Play of the Dice Game "Pig"](https://cupola.gettysburg.edu/cgi/viewcontent.cgi?article=1003&context=csfac)

## 🚀 Getting Started
The simplest way to play:
- Use `single_file_game`.
- Modify one or more of the players.
- Modify the `assign_points()` function.

👥 To play with friends or against other people:
- Fork this repl: [agentSIMX](https://replit.com/@SanjinDedic/agentSIMX).
- Use Replit in multiplayer mode. This allows each player to edit an agent and run a simulation.

## 🏠 How to Host a Game
To host the Greedy Pig Game Simulation, you will need:
- A Linux server (nginx or Apache2).
- Run `python3 api.py` to start the FastAPI application.
- For 24/7 agent reception, configure `systemd` to manage the FastAPI app as a service.
- Ensure all agents are located in the `classes` folder.
- To run a simulation:
  ```bash
  python3 live_table.py -sims 20000 -refresh 500
  ```

## 📚 Project Structure

### `player_base.py`

This file defines the `Player` class, which serves as the base class for all agents in the game. Key aspects include:

- **Initialization**: The `Player` class is initialized with a name, password, and default values for `banked_money`, `unbanked_money`, and `has_banked_this_turn`. 
- **Money Management**: Methods like `reset_unbanked_money()` and `bank_money()` manage the player's in-game finances.
- **Abstract Methods**: Being an abstract base class (ABC), it requires derived classes to implement specific methods, such as making game decisions.


### `multi_player_game.py`
Manages the game environment. Includes:
- **Game Setup**: Initializes with player objects.
- **Dice Class**: Simulates dice rolls.
- **Game Class**: Manages the game flow and scoring system.

### `agent_send.py`
Handles sending agents to the server. Includes:
- **HTTP Request**: Sends agent's code using POST.
- **Server Response**: Indicates agent acceptance and performance feedback.

### `animate_multi_player_game.py`
- Similar mechanics as `multi_player_game`.
- Features an interactive simulation table.
- Planned integration with `multi_player_game`.

## 🖥️ api.py
Serves as the backbone for agent validation and game management. Includes:

### Endpoints
- **Agent Upload**: For uploading agent files.
- **Simulation Trigger**: To start a simulation.
- **Status Check**: For current game status.

### Validation of Agents
Includes checks for script injection prevention, file system access control, and game logic adherence.

### Security Features
- **Rate Limiting**: To prevent API abuse.
- **CORS Middleware**: For secure cross-origin requests.
- **Error Handling**: For clear feedback and preventing sensitive information leakage.

## 📁 Repository Structure

```sh
└── agent_games/
    ├── agent_send.py
    ├── animated_multi_player_game.py
    ├── api.py
    ├── colors.json
    ├── live_table.py
    ├── multi_player_game.py
    ├── player_base.py
    ├── single_file_game.py
    ├── stress_tests/
    │   └── stress_test.py
    ├── teams.json
    ├── classes/
    │   └── .nothing
    ├── classes-by-strategy/
    │   ├── AI_Agent.py
    │   ├── . . 11 more player classes
    ├── test_classes/
    │   ├── AlwaysBank.py
    │   ├── . . 8 more player classes
    └── vcc_classes/
        ├── .nothing
        ├── AlwaysBank.py
        ├── . . 16 more player classes
```
