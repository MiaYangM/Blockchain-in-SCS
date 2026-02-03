# Blockchain in SCS

A demonstration of a permissioned blockchain with CRAB storage, zero-knowledge proofs, threshold signatures, smart contracts, performance benchmarking, and cross-border anchoring — adapted from the "Blockchain_in_SCS.ipynb" notebook.

## Features
- Permissioned blockchain (IBFT-2.0 simulation, 25 validators)
- CRAB storage model with RBAC (Create, Read, Append, Burn)
- zk-SNARK simulation (Groth16/BLS12-381-like flow)
- Threshold signatures and smart contract interface
- Performance benchmarking (latency, throughput, cost, error rate)
- Cross-border daily Merkle-root anchoring simulation
- Chain integrity verification and tamper detection demonstration

## Repo layout
```
blockchain-in-scs/
├─ src/blockchain_scs/
│  ├─ __init__.py
│  ├─ blockchain.py        # Part 1: PermissionedBlockchain
│  ├─ crab.py              # Part 2: CRABStorage with RBAC
│  ├─ zk.py                # Part 3: ZKProver
│  ├─ contracts.py         # Part 4: ThresholdSignature & SmartContract
│  ├─ perf.py              # Part 5: PerformanceBenchmark
│  ├─ anchoring.py         # Part 6: CrossBorderAnchoring
│  └─ demo.py              # Orchestration/prints mirroring the notebook
├─ notebooks/
│  └─ Blockchain_in_SCS.ipynb  # Your original notebook (unchanged)
├─ tests/
│  └─ test_basic.py
├─ .github/workflows/
│  └─ ci.yml               # Python tests CI
├─ .gitignore
├─ requirements.txt
├─ pyproject.toml
├─ Dockerfile
├─ LICENSE
└─ README.md
```

## Quickstart
1. Install
   ```
   python -m venv .venv
   source .venv/bin/activate  # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```
2. Run demo
   ```
   python -m blockchain_scs.demo
   ```
3. Run tests
   ```
   pytest -q
   ```
4. Open the notebook
   ```
   jupyter lab
   ```
   Then open `notebooks/Blockchain_in_SCS.ipynb`.

## Notebook-to-module mapping
- Part 1 → `src/blockchain_scs/blockchain.py`: `Transaction`, `Block`, `PermissionedBlockchain`
- Part 2 → `src/blockchain_scs/crab.py`: `UserRole`, `AccessCredential`, `CRABStorage`, `demonstrate_rbac()`
- Part 3 → `src/blockchain_scs/zk.py`: `ZKProver`
- Part 4 → `src/blockchain_scs/contracts.py`: `ThresholdSignature`, `SmartContract`
- Part 5 → `src/blockchain_scs/perf.py`: `PerformanceBenchmark`
- Part 6 → `src/blockchain_scs/anchoring.py`: `CrossBorderAnchoring`
- Demo orchestration → `src/blockchain_scs/demo.py`

Your original notebook remains unchanged in `notebooks/`. The modules reflect the same logical boundaries so you can gradually migrate code from the notebook to Python modules if you want a scripted flow.

## CI
GitHub Actions workflow `ci.yml` installs dependencies and runs `pytest`. It triggers on pushes and PRs to `main`.

## Docker
Build and run:
```
docker build -t blockchain-scs .
docker run --rm -it blockchain-scs
```

## License
MIT License.

## Maintainer
- MiaYangM

Last updated: 2026-02-03
