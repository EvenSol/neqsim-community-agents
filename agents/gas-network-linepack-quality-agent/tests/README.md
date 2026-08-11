# gas-network-linepack-quality-agent Validation Notes

Repository tests must confirm:

- all required package files and folders exist;
- AGENT.md front matter matches agent.yaml;
- all required skill IDs resolve in the vendored skills index;
- the manifest conforms to the shared schema;
- human review is required;
- the public example and reusable prompts are present;
- generated agent-skill and orchestration maps are current.

The companion Colab notebook retains seven successful code-cell executions, a
source-provenance record, one inspected PNG figure, and explicit screening
assertions. Engineering validity still requires the reviews named in AGENT.md.
