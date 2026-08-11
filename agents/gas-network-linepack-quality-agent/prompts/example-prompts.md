# Example Prompts

## Full Screen

```text
Use `gas-network-linepack-quality-agent` with public synthetic data to: Forecast a synthetic high-CO2 source front and demand step through three pipe sections to the delivery node.
Show the declared skill sequence, unit checks, assumptions, results, uncertainty,
contradictory evidence, limitations, and human-review gates.
```

## Missing-Data Screen

```text
Use `gas-network-linepack-quality-agent` to inspect this incomplete public input package. Do not fill
material gaps silently. Return the minimum additional data, safe screening cases,
and which conclusions must remain open.
```

## Independent Review

```text
Review this existing screening package using `gas-network-linepack-quality-agent`. Check skill
traceability, units, reference conditions, assumptions, failed or marginal cases,
and whether the proposed next action is supported at screening level.
```
