# clone-lin-curve-stableswap

Original **LIN** clone of the Curve 3pool StableSwap quote kernel
(`get_D`, `get_y`, `get_dy`).

- **Class:** EXPERIMENTAL (real published algorithm, uint64-scale operands ~1e10)
- **Not claimed:** mainnet uint256 / 3pool parity, TVL, or replacing Curve
- **LIN source:** [`src/lin_curve_stableswap.lin`](src/lin_curve_stableswap.lin)
- **Proofs (auditable):** [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open) — `examples/curve_stableswap/` and `test/prove_curve_stableswap_external.py`
- **Compiler 0:** C11 `transpile/c/bin/lin_c0` in lin-open (no Zig required to run the clone)

## What is different from the Vyper pool

1. Amplification `A`, balances, and `fee` are function arguments (no hidden storage / `block.timestamp` ramp).
2. `(a*b + c)/d` uses a 128-bit product; quotient overflow fail-closes to 0.
3. Zero coin / zero A / division by zero fail-closed to 0.

See `NOTICE` for upstream citation. This tree does not contain Curve's Vyper.
