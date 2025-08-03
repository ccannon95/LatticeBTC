# 🧱 LatticeBTC

**LatticeBTC** is a proof-of-concept cryptocurrency designed to test a scalable, quantum-resistant mining model using a lattice-constrained proof-of-work system. It keeps the core logic of Bitcoin (block structure, SHA256 hashing, halving, capped supply) but introduces a new dimension to block validation — a **spatial coordinate constraint** that dramatically hardens the system against brute-force and quantum attacks.

---

## ⚙️ Core Parameters

| Parameter         | Value                              |
|------------------|------------------------------------|
| Max Supply        | **5,376,000,000 coins**            |
| Block Time        | **2.343 seconds**                  |
| Halving Interval  | **53,760,000 blocks (~4 years)**   |
| Decimal Places    | **8** (same as Bitcoin)            |
| Block Size Limit  | **2.56 MB**                        |
| Block Reward      | **Starts at 50**, halves every 4 years |
| Mining Algorithm  | **SHA256 + Lattice Constraint**    |

---

## 🔐 Why LatticeBTC?

Current Bitcoin miners brute-force nonces to find a block hash below a given target. LatticeBTC **preserves this structure**, but adds a spatial filter:

> The hash must land at a valid **X, Y, Z** coordinate in a **256×256×256 cube** (16,777,216 unique points). Only hashes at a target coordinate (or line/plane range) are accepted.

This gives us a second layer of difficulty beyond just the hash target — a **coordinate gate**. It:

- ⛓️ Makes preimage and collision attacks useless without coordinate match
- 🔐 Increases resilience against quantum brute-forcing (e.g., Grover's)
- ⚡ Spreads mining difficulty across space instead of just entropy

---

## 🧠 Technical Overview

### Block Mining:

1. **Header Creation:**
   - Block hash uses SHA256 of block header + nonce (like Bitcoin)
2. **Lattice Mapping:**
   - First bytes of hash mapped to `(x, y, z)` coordinates:
     ```c++
     x = hash[0] % 256
     y = hash[1] % 256
     z = hash[2] % 256
     ```
3. **Validation Filter:**
   - Only blocks that land on an **active coordinate, line, or plane** are accepted
   - Active zone can be adjusted per epoch

### Difficulty Adjustment:

- Uses the **same logic as Bitcoin**:
  - Targets 2.343 seconds per block
  - Every **2016 blocks**, difficulty readjusts to match real-world block time
- Lattice filters can **scale up** (more constraints) or **scale down** (relax filters) as needed

---

## 🧪 Quantum Resistance, Explained

Traditional PoW (SHA256) can eventually be weakened by quantum algorithms. LatticeBTC responds by:

- Adding a **spatial constraint** that’s orthogonal to raw hashing
- Making collisions or shortcut attacks useless unless the **coordinates match**
- Enabling **dynamic lattice growth** — increasing difficulty without rehashing the algorithm

---

## 🎯 Goals

- 🚀 Serve as a **testnet for lattice-constrained consensus**
- 👷‍♂️ Stress-test miner diversity, speed, and distribution
- 🔬 Simulate quantum-resilient design in a public memecoin setting
- 🧰 Provide an upgrade path for legacy SHA256 systems

---

## 🛠️ Roadmap

- [x] Miner prototype (SHA256 + lattice match)
- [ ] Full blockchain prototype (Go/C++)
- [ ] Faucet + explorer for LatticeBTC testnet
- [ ] Dual-mining client (BTC-compatible, Lattice-enhanced)
- [ ] Publish whitepaper & security model

---

## 🤖 Status

**LatticeBTC is under active development.**

This is a research project and memecoin rolled into one. The lattice constraint model can be ported to other chains, and performance benchmarks are ongoing.

---

## 🧙 Inspiration

Inspired by:
- Bitcoin (obviously)
- Quantum threat modeling (Grover’s, Shor’s)
- Lattice cryptography
- Minecraft (don’t lie — you thought of it too)
- The phrase “dumb idea, but what if it works?”

---

## 🧾 License

Free to use, fork, rewrite, or mine into oblivion (If you can).
