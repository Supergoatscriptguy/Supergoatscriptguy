# Hi, I'm Supergoatscriptguy

I like building things from scratch to see how they actually work. So far that's
been a chess engine in C++, and now a language model written in assembly.

## Mnemonic

A chat language model written entirely in assembly: x86-64 (NASM) on the CPU and
hand-written PTX on the GPU. No Python, no PyTorch, no CUDA toolkit, no libraries.
Just the Win32 API and the NVIDIA driver.

Everything between the raw dataset and the trained model is in the repo:

- a parquet reader with its own zstd and snappy decompressors, for FineWeb-Edu
- a byte-level BPE tokenizer (32K vocab), trained and run in assembly
- the CUDA driver API called straight from asm, with tensor-core matmuls and
  flash attention written in PTX
- a Llama-style transformer (RoPE, RMSNorm, SwiGLU, grouped-query attention)
  whose backward pass is checked against finite differences
- a trainer with AdamW, a live progress bar, and checkpoints that resume bit for bit

Pretraining the 126M-parameter model on 5B tokens takes about 20 hours on one
RTX 5070 Ti, at around 60 TFLOPS. Next up: chat fine-tuning, int8/int4
quantization, and a chat program that runs on the CPU.

**[github.com/Supergoatscriptguy/Mnemonic](https://github.com/Supergoatscriptguy/Mnemonic)**

## IxEngine

A UCI chess engine written from nothing in C++17: bitboards with magic sliders, a
principal-variation search with the usual modern pruning, Lazy SMP, and an NNUE
evaluation trained only on its own self-play games.

It plays at about **3200 on the CCRL blitz scale** (±24), measured with a 400-game
gauntlet against rated engines on one thread:

| Opponent | CCRL | IxEngine |
|:--|:--:|:--:|
| Halogen 10 | 3194 | 56% |
| Weiss 2.0 | 3265 | 43% |
| Zahak 10.0 | 3292 | 37% |
| Alexandria 3.5 | 3321 | 24% |

It went from about 3090 to 3200 over the summer, one SPRT-tested change at a time.
Every change, kept or thrown away, is written up in
[TESTING.md](https://github.com/Supergoatscriptguy/IxEngine/blob/main/TESTING.md).

​```
board    bitboards, fancy magics, Zobrist keys, perft-exact move generation
search   PVS, aspiration windows, null move, LMR, RFP/LMP/SEE pruning,
         singular extensions with multicut, history-based move ordering
threads  Lazy SMP with a weighted best-move vote
eval     768→512 NNUE, SCReLU, 8 output buckets, AVX2, built into the exe
​```

It was my first real systems project after a lot of Python, and still the one
I've had the most fun with.

**[github.com/Supergoatscriptguy/IxEngine](https://github.com/Supergoatscriptguy/IxEngine)**

## Tools

C++, x86-64 assembly (NASM), PTX / CUDA, Python, PyTorch, NumPy.
