# Blackjack with GUI

A desktop Blackjack game written in Python with a graphical interface built using wxPython.

The project implements the core Blackjack game loop, card and deck management, multiple local players, dealer AI, bankroll tracking, graphical card rendering, and basic experimental TCP networking code.

## Tech Stack

- Python
- wxPython
- Object-Oriented Programming
- Python sockets
- Standard library modules: `random`, `socket`, `os`

## Features

- Graphical Blackjack table
- Support for 1 to 4 local players
- Custom player names
- Dealer AI
- Hit and Stand actions
- Automatic Blackjack hand scoring
- Correct Ace handling as 1 or 11
- Blackjack and bust detection
- Player bankroll tracking
- Multiple rounds
- Card rendering with suit images
- Hidden dealer card during player turns
- New Game / Play Again flow
- Basic host/client TCP networking prototype

## Game Overview

At the start of a new game, the player can choose the number of participants and enter player names.

Each player starts with a bankroll of:

```text
$1000
```

The dealer starts with:

```text
$2000
```

A shuffled 52-card deck is created and two cards are dealt to every participant.

During a player's turn, the available actions are:

- **Hit** — draw another card
- **Stand** — finish the current turn

Once all players finish their turns, the dealer plays automatically.

The dealer continues drawing cards while its hand value is 16 or lower.

## Blackjack Scoring

Number cards use their numeric value.

Face cards are worth 10 points:

- Jack = 10
- Queen = 10
- King = 10

Aces initially count as 11.

If the hand would exceed 21, Aces are automatically converted from 11 to 1 when necessary.

For example:

```text
Ace + 9 = 20
Ace + 9 + 5 = 15
```

## Project Structure

```text
BlackJack_with_gui/
│
├── main.py
├── README.md
│
└── suites/
    ├── blank.png
    ├── club.png
    ├── diamond.png
    ├── heart.png
    ├── spade.png
    └── readme2.txt
```

## Main Classes

### MainWindow

Creates the main application window and provides menu actions for:

- starting a new game
- hosting a network connection
- joining a network connection
- displaying application information
- closing the application

### NewGamePrompt

Handles game setup.

The player can select between 1 and 4 players and provide player names before starting a game.

### Table

Controls the main game flow and GUI rendering.

Responsibilities include:

- creating players and dealer
- starting rounds
- switching turns
- drawing cards on screen
- handling Hit and Stand actions
- calculating round results
- updating bankrolls
- checking whether players are out of money
- starting a new round

### Deck

Represents a standard 52-card deck.

It supports:

- deck creation
- shuffling
- removing the top card
- returning discarded cards to the deck

### Player

Represents a Blackjack player.

Each player stores:

- name
- current hand
- bankroll
- game state

The class also contains logic for drawing cards, discarding a hand, and calculating hand value.

### AI

Extends the `Player` class and represents the dealer.

The dealer automatically draws cards while its hand value is 16 or lower.

## Object-Oriented Design

The project uses several classes to separate different responsibilities:

```text
MainWindow
    │
    ├── NewGamePrompt
    │
    └── Table
          │
          ├── Deck
          ├── Player
          └── AI
               └── inherits from Player
```

This separates GUI management, game state, card logic, player behavior, and dealer behavior.

## GUI

The graphical interface is implemented with wxPython.

Cards are drawn directly onto the game panel, while suit images are loaded from the `suites/` directory.

The dealer's first card is hidden during player turns using:

```text
suites/blank.png
```

The application window size is:

```text
800 x 600
```

## Networking Prototype

The repository also contains basic TCP socket code for hosting and connecting to another machine.

The networking implementation uses:

```text
socket.AF_INET
socket.SOCK_STREAM
```

and port:

```text
5084
```

This part of the project is an experimental networking prototype and is separate from the main local Blackjack gameplay.

## Requirements

- Python 3
- wxPython

Install wxPython with:

```bash
pip install wxPython
```

## Running the Project

Clone the repository:

```bash
git clone https://github.com/Sunnez/BlackJack_with_gui.git
```

Move into the project directory:

```bash
cd BlackJack_with_gui
```

Install the GUI dependency:

```bash
pip install wxPython
```

Run the application:

```bash
python main.py
```

Keep the `suites` directory in the project root because the application loads card suit images from it at runtime.

## What This Project Demonstrates

This project demonstrates practical experience with:

- Python programming
- object-oriented programming
- inheritance
- GUI application development
- event-driven programming
- game-state management
- class-based application design
- basic AI behavior
- card-game logic
- file-based graphical assets
- basic TCP socket programming
