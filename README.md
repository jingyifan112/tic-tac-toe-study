# Tic-Tac-Toe Study

This repository documents my study and local run of a small reinforcement learning project that trains a simple neural network to play tic-tac-toe using C.

## Source

Original article and code: Arthur Chiao's tic-tac-toe reinforcement learning project.

This repository is my personal study and reproduction record. The original implementation is not my work. I used it to understand the neural network and reinforcement learning pipeline, then documented my run process and results.

## What I studied

The project implements a simple neural network for tic-tac-toe:

- The 3x3 board is encoded into an 18-dimensional input vector.
- The neural network has one hidden layer with 100 hidden units.
- The output layer has 9 values, corresponding to the 9 board positions.
- A softmax function converts the raw outputs into move probabilities.
- During training, the neural network plays against a random opponent.
- After each game, the final result is used as a reward signal.
- The model updates its weights through backpropagation.
- The trained model is saved as `ttt_nn.bin`.
- The play program loads the saved model and allows human-vs-computer play.

## Main files reviewed

The original project contains three main files:

- `common.h`: shared game state, neural network structure, board encoding, forward pass, and move selection.
- `train.c`: initializes the neural network, trains it against random games, and saves the trained parameters.
- `play.c`: loads the trained neural network and starts the interactive tic-tac-toe game.

## How I ran it

I first tried to compile the project using the original `make` workflow. On macOS, the original Makefile command included `common.h` as a compiler input, which caused a clang error. I then compiled the two C files manually:

```bash
cc train.c -o train -O3 -Wall -W -ffast-math -lm
cc play.c -o play -O3 -Wall -W -ffast-math -lm
```

After compilation, I ran a quick training test:

```bash
./train 10000
```

Then I ran a larger training session:

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

## Run logs

I saved terminal outputs in the `run_logs/` folder:

- `make.log`: manual compilation output on macOS
- `train_10000.log`: quick training test output
- `train_2000000.log`: full training output
- `model_file_after_10000.log`: model file check after quick training
- `play.log`: interactive play output or play-mode note

## Screenshot

The `screenshots/` folder contains a terminal screenshot of the interactive play demo.

## Result

I successfully compiled the C code, trained the tic-tac-toe neural network, generated the model file, and tested the interactive play mode in the terminal.

In the 2,000,000-game training run, the model reached a high win rate against the random opponent and saved the trained neural network to `ttt_nn.bin`.

## Learning summary

The full pipeline is:

```text
board state
-> input encoding
-> neural network forward pass
-> move probability output
-> choose the best legal move
-> finish one game
-> assign reward based on win/draw/loss
-> backpropagation
-> update weights
-> save trained model
-> load model for interactive play
```

## Next steps

If I have more time, I would like to:

- Compare model behavior after different training game counts.
- Study the reward design in more detail.
- Modify the hidden layer size and observe the effect.
- Review the backpropagation implementation line by line.
