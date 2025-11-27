# A repository of all the "bright" ideas I have.

1. Implement an OS for arduino.
2. Create a text editor for said OS (based on ed).
3. Figure out a way to implement the multiplication based hashing scheme in
rust.
4. Minesweeper for the terminal.
5. Calorie tracker.
6. Traceroute.
7. Create a graph view generator for markdown files.
    - Optimize it using caching/compression.
8. Airdrop.
9. Optimize the new-session script.
    - Set a variable for the current directory.
    - Make it run ssh-agent if the directory contains a git repository.
10. LLM in C
11. LFS - Linux from scratch
12. Terminal based battleship that can be played over wireless LAN.
13. Redstone battleship in minecraft.

# Software Standards Implementation Roadmap (Rust and C)

This roadmap outlines how to implement 10 software standards to maximize
conceptual learning, minimize overlap, and build experience in complex software.
It is designed for programmers familiar with language basics but new to
building non-trivial systems. Projects are split between C and Rust based on
system-level learning and safe abstractions.

-------------------------------------------------------------------------------

## 1. Approach Overview

### Three-Layer Method
1. *Understand* – Study the problem the standard solves. Read overview
   sections, examine a small reference implementation, and sketch the system.
2. *Scaffold* – Build a minimal working version. Hard-code valid examples and
   replace constants with real logic. Use Result<T, E> (Rust) or structured
   error handling (C) early and test modules.
3. *Refine & Verify* – Expand correctness. Add tests, compare against real
   tools, and support optional features incrementally.

### Best Practices
- Modularize code and keep functions small.
- Run formatters and linters regularly (cargo fmt/clippy in Rust).
- Version-control aggressively with small commits.
- Document design decisions and lessons learned after each project.

### Frustration Control
| Symptom | Cause | Fix |
|----------|--------|-----|
| Stuck reading spec | Too abstract | Implement one valid example first |
| Compiler fights | Too generic early | Start concrete, refactor later |
| Lost motivation | Too many unknowns | Add small visible wins |
| Forget context | Domain switching | Keep a short project diary |

-------------------------------------------------------------------------------

## 2. Project Roadmap (C and Rust)

| Stage | Standard | Language | Complexity Focus |
|-------|----------|----------|----------------|
| 1 | DNS (Domain Name System) | C | Binary parsing, structs, sockets, byte-level correctness |
| 1 | HTTP/1.1 | Rust | Client-server design, modular functions, error handling |
| 1 | JSON Parser | Rust | Recursive data structures, enums, error propagation |
| 1 | WebSocket Protocol | Rust | Async communication, message framing, concurrency patterns |
| 2 | WAV Reader (Header Only) | C | Memory allocation, file I/O, endian handling |
| 2 | ZIP (Small File) | C | Compression/decompression, buffers, algorithm implementation |
| 2 | ELF Parser (Header Only) | C | File layout, memory alignment, binary parsing |
| 2 | PNG Decoder (Header & First Chunk) | Rust | Modular parsing, slices, error handling |
| 3 | SQLite Minimal Subset | Rust | Data parsing, storage logic, modularity |
| 3 | SMTP (Minimal Send Only) | Rust | Networking, modular design, safe concurrency |

-------------------------------------------------------------------------------

## 3. Phase Plan

### Phase 1 (Weeks 1–3)
*DNS → HTTP/1.1 → JSON Parser → WebSocket Protocol*  
Focus: Networking, basic protocols, recursive data structures, async communication.

### Phase 2 (Weeks 4–6)
*WAV → ZIP → ELF → PNG Decoder*  
Focus: File formats, memory management, binary parsing, modular design.

### Phase 3 (Weeks 7–10)
*SQLite → SMTP*  
Focus: Storage, parsing, modular systems, concurrency, and networking.

-------------------------------------------------------------------------------

## 4. Implementation Framework Example (JSON Parser in Rust)

### Stage 1: Understand
- Identify main entities: objects, arrays, values.
- Sketch parse flow: input → tokens → tree → serialize back.

### Stage 2: Scaffold
- Define enum JsonValue { Null, Bool, Number(f64), String(String), Array(Vec<JsonValue>), Object(HashMap<String, JsonValue>) }.
- Hard-code parsing of a single valid JSON like {"key": "value"}.
- Print the internal structure for inspection.

### Stage 3: Refine & Verify
- Implement string escaping, number parsing, and error handling.
- Write property-based tests using proptest:
  encode → decode → encode must be stable.
- Compare output with serde_json.

Deliverable: minimal but correct JSON parser and s
