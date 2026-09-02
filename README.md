<a href="https://github.com/Supergoatscriptguy">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=500&size=28&pause=1000&color=58A6FF&vCenter=true&width=500&lines=Hey%2C+I'm+Supergoatscriptguy;I+build+a+chess+engine" alt="Typing SVG" />
</a>

I like building things from scratch to understand how they work. Right now that
means a chess engine in C++ — the search, the board, the evaluation network, the
testing rig, all of it — and I'll automate anything that annoys me enough.

---

### ♟ IxEngine

A UCI chess engine written from nothing in C++17. No engine libraries, no
borrowed nets: bitboards with magic sliders, a principal-variation alpha-beta
search with the modern pruning stack, Lazy SMP, and an NNUE evaluation trained
entirely on the engine's own self-play games.

[![IxEngine](https://img.shields.io/badge/IxEngine-View_Repo-58A6FF?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Supergoatscriptguy/IxEngine)
[![Version](https://img.shields.io/badge/version-1.1-58A6FF?style=for-the-badge)](https://github.com/Supergoatscriptguy/IxEngine)
[![Strength](https://img.shields.io/badge/CCRL_blitz-~3200-58A6FF?style=for-the-badge)](https://github.com/Supergoatscriptguy/IxEngine/blob/main/TESTING.md)
[![Language](https://img.shields.io/badge/C%2B%2B17-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)](https://github.com/Supergoatscriptguy/IxEngine)

**How strong.** Measured with a 400-game gauntlet against engines with published
CCRL ratings, one thread, blitz:

| Opponent | CCRL | IxEngine |
|:--|:--:|:--:|
| Halogen 10 | 3194 | 56% |
| Weiss 2.0 | 3265 | 43% |
| Zahak 10.0 | 3292 | 37% |
| Alexandria 3.5 | 3321 | 24% |

That works out to **≈3198 (±24)** on the CCRL blitz scale. The number has moved
from ~3090 to ~3200 over the summer, one SPRT-gated patch at a time — every
change, kept or thrown away, is written up in
[TESTING.md](https://github.com/Supergoatscriptguy/IxEngine/blob/main/TESTING.md).

**What's inside.**

```
board      bitboards · fancy magic sliders · Zobrist keys · perft-exact movegen
search     PVS · aspiration · null move · LMR · RFP/LMP/SEE pruning
           singular extensions with multicut + double extensions
           TT move → captures → killers → countermove → continuation history
threads    Lazy SMP, staggered helper depths, weighted best-move vote
eval       768→512 NNUE, SCReLU, 8 output buckets, AVX2, compiled into the exe
           bootstrapped over two self-play generations (+240 Elo over the hand eval)
testing    self-play SPRT at two time controls · CCRL-anchored rating gauntlet
```

**How it got here.**

```
hand eval, bitboards, PVS ─► NNUE gen1 (self-play, +124) ─► gen2 (+237)
        ─► singular extensions, time management, countermoves, continuation history
        ─► embedded net, tuned extensions, history fix (+74), SMP voting ─► 1.1
```

My first proper systems project after a lot of Python, and easily the one I've
had the most fun with.

---

### Stuff I Use

[![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)](https://isocpp.org/)
[![CMake](https://img.shields.io/badge/CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white)](https://cmake.org/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![VS Code](https://img.shields.io/badge/VS_Code-007ACC?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iI2ZmZiIgZD0iTTIzLjE1IDIuNTg3IDE4LjIxLjIxYTEuNDk0IDEuNDk0IDAgMCAwLTEuNzA1LjI5bC05LjQ2IDguNjMtNC4xMi0zLjEyOGEuOTk5Ljk5OSAwIDAgMC0xLjI3Ni4wNTdsLS45OS45MThhLjk5OC45OTggMCAwIDAgMCAxLjUwNmwzLjU4IDMuMjctMy41OCAzLjI3YS45OTguOTk4IDAgMCAwIDAgMS41MDZsLjk5LjkxOGMuMzUuMzIzLjg3LjM2NyAxLjI3Ni4wNTdsNC4xMi0zLjEyOCA5LjQ2IDguNjNhMS40OTIgMS40OTIgMCAwIDAgMS43MDQuMjlsNC45NDItMi4zNzdhMS40OTYgMS40OTYgMCAwIDAgLjg1LTEuMzVWMy45MzdhMS40OTUgMS40OTUgMCAwIDAtLjg1LTEuMzV6bS02LjYzIDEzLjY2M0w5LjU0IDEybDYuOTgtNC4yNXY4LjV6Ii8+PC9zdmc+&logoColor=white)](https://code.visualstudio.com/)
[![PyCharm](https://img.shields.io/badge/PyCharm-000000?style=for-the-badge&logo=pycharm&logoColor=white)](https://www.jetbrains.com/pycharm/)

---

[![Snake animation](https://raw.githubusercontent.com/Supergoatscriptguy/Supergoatscriptguy/refs/heads/main/snake_faded.svg)](https://github.com/Supergoatscriptguy)
