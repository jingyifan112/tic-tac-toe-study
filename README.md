# tic-tac-toe-study

This repo documents my study and reproduction of a small tic-tac-toe reinforcement learning project written in C.

The original implementation is from Arthur Chiao's tic-tac-toe reinforcement learning example. I used it as a learning project to understand how a simple neural network can be trained to play tic-tac-toe through repeated games and reward-based updates.

## Overview

The project trains a small neural network to play tic-tac-toe:

- The 3x3 board is encoded as neural network input.
- The model outputs probabilities for the 9 possible move positions.
- During training, the model plays against a random opponent.
- After each game, the win/draw/loss result is used as the reward signal.
- The model updates its weights through backpropagation.
- The trained model is saved as `ttt_nn.bin`.
- The `play` program loads the trained model for interactive play.

## Files reviewed

The main files in the original project are:

- `common.h`: shared game logic, neural network structure, board encoding, forward pass, and move selection
- `train.c`: model initialization, training loop, reward-based learning, and model saving
- `play.c`: loading the trained model and running the interactive game

## Reproduction steps

I compiled the training and play programs locally with:

```bash
cc train.c -o train -O3 -Wall -W -ffast-math -lm
cc play.c -o play -O3 -Wall -W -ffast-math -lm
```

Then I ran a short training test:

```bash
./train 10000
```

After confirming the training process worked, I ran a larger training session:

```bash
./train 2000000
```

This generated the trained model file:

```bash
ttt_nn.bin
```

Finally, I tested the interactive play mode:

```bash
./play
```

## Results

The code compiled successfully, the model trained successfully, and the interactive tic-tac-toe play mode ran in the terminal.

The `run_logs/` folder contains the compilation and training logs, and `screenshots/play_demo.png` shows the interactive play demo.

## Learning summary

This project helped me understand the basic reinforcement learning workflow in a small and readable C implementation:

```text
board state
-> input encoding
-> neural network forward pass
-> move probability output
-> legal move selection
-> game result
-> reward signal
-> backpropagation
-> weight update
-> saved model
-> interactive play
```
