# ViCTORIA


ViCTORIA is a UCI chess engine built from scratch using C++ 20.

It performs an in-depth analysis and uses a handcrafted evaluation function to evaluate each chess board.

It can perform an analysis in reasonable (10-25 seconds) time between depth 6 and 10+, depending on the number of possible moves.

Its elo rating is 1694 in blitz (February 2021).

ViCTORIA is not a complete chess program and requires a UCI-compatible graphical user interface (GUI) (e.g. XBoard with PolyGlot, Scid, Cute Chess, eboard, Arena, Sigma Chess, Shredder, Chess Partner or Fritz) in order to be used comfortably.

If you want to see a better version of ViCTORIA powered by deep learning check out [Deep ViCTORIA](https://github.com/LE10EENFAIT/Deep-ViCTORIA).

## Build
ViCTORIA is built from scratch, so you don't need any C++ library, only a compiler (min C++ 17).

You need [CMake](https://cmake.org/).
On Windows you can use [Cygwin](https://www.cygwin.com/) to install ```g++``` and ```make```.

Then: 
```bash
mkdir build
cd buid
cmake ..
make
```

In the future, I will provide binaries.

## Usage
```bash
./ViCTORIA
```
UCI commands:
+ `position startpos [moves move_list]`
+ `position fen your_fen [moves move_list]`
+ `go depth n`
+ `go infinite`: search until you enter `stop`
+ `go movetime t`: search for t milliseconds
+ `go wtime t1 btime t2 [winc t3 binc t4]`: Whites has `t1` ms on clock Blacks has `t2` ms on clock. Whites increment their time by `t3` ms and Blacks increment their time by `t4` ms
+ `go nodes n` search for n nodes (In fact, the number of nodes explored will be a bit greater than *n*)  
+ `set openings path` use the openings book at path (must be in UCI format)

## Evaluation function
Among other thing, the evaluation function takes into account:
+ Material score
+ Pieces/squares tables
+ Different evaluation for end game (differents pieces/position tables, pawn value is slightly increased, etc...)

## Features
+ Alpha-Beta pruning
+ Magic bitboard for sliding pieces
+ Iterative deepening
+ Aspiration windows
+ Move ordering
    + Captures table
    + Killer move heuristic
+ ~~Transposition table with Zobrist's hashing function (1 000 000 positions ~ 50 Mb)~~
+ Openings book

## License
[GPL v3](https://choosealicense.com/licenses/gpl-3.0/)
