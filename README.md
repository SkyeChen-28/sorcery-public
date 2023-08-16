# sorcery-public

## About

A strategy card game based on collectible card games such as "Hearthstone: Heroes of Warcraft" and "Magic: the Gathering". 

This game was a deliverable for the course "Object-Oriented Software Development" which I took during my Winter 2023 term during my studies at the University of Waterloo. The game was written fully in C++ in collaboration with Connor Baetz and Jongwoo Shin. As per our instructors' request, the source code cannot be posted publicly, but can be provided to potential employers upon request. 

## Requirements

### Environment

This game was developed in, and runs best in the following Debian/Linux environment/version:

```
cat /etc/*release
Output:
PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```

```
cat /etc/*version
Output:
11.6
```

```
uname -srm
Output:
Linux 5.15.90.1-microsoft-standard-WSL2 x86_64
```

### Installation

1. Download the folder "game_files"
2. Open up a terminal and `cd` to that folder
3. Grant the file `sorcery` execution permissions:

```
chmod u+x sorcery
```

4. Run the following command:

```
./sorcery
```

## How to Play

### Objective

The objective of the game is to reduce the opposing player's life to 0. 

### Cards

You can achieve this objective by using your cards. Each card is one of following four classes:

#### 1. Spells

The simpliest type of card. When played, a spell changes the game in some way (such as destroying a minion or ritual) and is then removed from the game. 

#### 2. Minions

The main card type, and the primary way to achieve victory. When played, a minion stays on the board until it's defense goes to zero. It has an attack value that can be used to attack other minions or the opposing player. Minions also have actions and abilities. Actions tell it how many things it can do per turn, abilities have special effects on gameplay.

#### 3. Enchantments

Enchantments are modifications that can be played on minions. They can modify anything from attack/defense values, or grant them new abilities. Enchantments stack in oldest-to-newest order. 

#### 4. Rituals

Rituals are special cards with a triggered ability, an activation cost, and a number of charges. To trigger a ritual's abilities, it expends a number of charges equal to it's activation cost. A player may only have at most one ritual on the baord at any time. 

### Commands

Type `help` to obtain the following help message:

```
Commands: help -- Display this message.
          end  -- End the current player's turn.
          quit -- End the game.
          attack minion other-minion -- Orders minion to attack other-minion.
          attack minion -- Orders minion to attack the opponent.
          play card [target-player target-card] -- Play card, optionally targeting target-card owned by target-player.
          use minion [target-player target-card] -- Use minion's special ability, optionally targeting target-card owned by target-player.
          inspect minion -- View a minion's card and all enchantments on that minion.
          hand -- Describe all cards in your hand.
          board -- Describe all cards on the board.
```

#### Attack

The `attack` command follows one of two formats:

- `attack i` orders minion `i` to attack the opposing player, where 1 is the leftmost minion and 5 is the rightmost minion.
- `attack i j` orders the active player’s minion `i` to attack the inactive player’s minion `j`, where both `i` and `j` are as above.

#### Play

The `play` command follows one of two formats:

- `play i` plays the `i`th card in the active player’s hand with no target. For example, this can be used to play minions,
rituals, and spells with no targets. Note that `i` ranges from 1 to 5.
- `play i p t` plays the `i`th card in the active player’s hand on card `t` owned by player `p`. `p` may be equal to 1 or 2 to
represent player 1 or 2 respectively (1 is the top player, 2 is the bottom player). `t` is either 1, 2, 3, 4, 5 (the `i`th minion owned by player `p`) or `r` (the ritual
owned by player `p`). This can be used to play enchantments and spells with targets.

#### Use

The `use` command follows the same format as the `play` command and has the same meaning, except that `i` refers to the `i`th
minion owned by the current player, and the command orders that minion to use its activated ability on the provided target (or
on no target).


### Playing the game

1. Enter the names of the two players playing.
2. Execute player 1's moves, then `end`.
3. Execute player 2's moves, then `end`.
4. Repeat steps 2 and 3 until there is a winner.

### Tips

- It is helpful to regularly display the `board` and your `hand` throughout the game, at the start of every turn, and as frequently as you need it.

For further details about this project's deliverables, criteria, and expectations; see the file [Sorcery.pdf](https://github.com/SkyeChen-28/sorcery-public/blob/main/Sorcery.pdf)