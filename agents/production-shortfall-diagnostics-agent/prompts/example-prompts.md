# Example Prompts

## Full Screen

```text
Use `production-shortfall-diagnostics-agent` with public synthetic data to: Diagnose a 9 percent synthetic gas-condensate production shortfall after a pressure-drop event and rank flowline, compressor, well-inflow, and allocation explanations.
Show the declared skill sequence, unit checks, assumptions, results, uncertainty,
contradictory evidence, limitations, and human-review gates.
```

## Missing-Data Screen

```text
Use `production-shortfall-diagnostics-agent` to inspect this incomplete public input package. Do not fill
material gaps silently. Return the minimum additional data, safe screening cases,
and which conclusions must remain open.
```

## Independent Review

```text
Review this existing screening package using `production-shortfall-diagnostics-agent`. Check skill
traceability, units, reference conditions, assumptions, failed or marginal cases,
and whether the proposed next action is supported at screening level.
```
