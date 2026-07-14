# PyMemSim-Agent

![PyMemSim-Agent](https://drive.google.com/uc?export=view&id=1FsAc9xSPgdPoz_HH4f4ZkyYukjNRoxir)

PyMemSim-Agent is a harness-neutral instruction and workflow repository for AI-assisted chemical-engineering membrane simulation. It is designed to give Codex, Claude, Gemini, and other AI coding or research agents the same scientific rules, workflow files, examples, and thermodynamic-reference skill needed to orchestrate reproducible PyMemSim-MCP simulations.

The repository does not implement the membrane solver itself. Instead, it defines how an AI agent should prepare structured inputs, validate thermodynamic references, call the PyMemSim MCP tools, and report results without inventing scientific data or bypassing the deterministic simulation backend.

## What This Repository Provides

- Repository-level agent policy in `AGENTS.md`.
- Harness-neutral scientific workflows in `workflows/`.
- Agent-specific skill copies for Codex, Claude, and Gemini.
- MCP configuration examples for PyMemSim-MCP.
- Prompt templates for thermodynamic reference generation.
- Hollow-fiber membrane validation cases and experimental comparison data.
- A structured thermodynamic property reference document in `data/`.

## Architecture

The intended workflow separates agent-facing preparation from scientific execution:

```text
User request
  -> AI harness reads AGENTS.md and the relevant workflow
  -> Agent prepares or validates reference_content
  -> Agent prepares conventional process and membrane inputs
  -> PyMemSim-MCP validates and executes the selected tool
  -> PyThermoDB / PyThermoLinkDB build runtime model objects internally
  -> PyCUC performs internal unit harmonization
  -> PyMemSim performs deterministic membrane simulation
  -> Agent reports structured results, assumptions, diagnostics, and limitations
```

The key boundary is that the agent supplies `reference_content` and conventional inputs. The agent must not manually build, expose, or pass the internal runtime `model_source` unless a live MCP tool schema explicitly requires it.

## Repository Layout

```text
.
|-- AGENTS.md
|-- README.md
|-- .codex/
|   |-- config.toml
|   `-- skills/pythermodb-reference-maker/
|-- .claude/
|   `-- skills/pythermodb-reference-maker/
|-- .gemini/
|   |-- settings.json
|   `-- skills/pythermodb-reference-maker/
|-- data/
|   `-- thermodynamic_property.md
|-- examples/
|   |-- case-1.md
|   |-- case-2.md
|   |-- case-3.md
|   `-- validation data/
|-- prompts/
|   |-- prompt-1.md
|   |-- prompt-2.md
|   |-- prompt-3.md
|   `-- prompt-4.md
`-- workflows/
    |-- membrane-simulation.md
    |-- reference-content-generation.md
    `-- sensitivity-analysis.md
```

## Harness Support

This repository is intentionally structured so multiple AI harnesses can consume the same scientific workflow.

### Codex

Codex uses:

- `AGENTS.md` for repository-level behavior and scientific safety rules.
- `.codex/config.toml` for MCP server configuration.
- `.codex/skills/pythermodb-reference-maker/` for thermodynamic YAML generation.

The included Codex MCP configuration is:

```toml
[mcp_servers.pymemsim_mcp]
command = "uvx"
args = ["pymemsim-mcp", "--mode", "stdio"]
```

### Claude

Claude-oriented skill files are mirrored in:

```text
.claude/skills/pythermodb-reference-maker/
```

Use the same repository instructions in `AGENTS.md` and the workflow files in `workflows/`.

### Gemini

Gemini-oriented settings and skill files are mirrored in:

```text
.gemini/settings.json
.gemini/skills/pythermodb-reference-maker/
```

The Gemini MCP settings point to the same expected PyMemSim-MCP command:

```json
{
  "mcpServers": {
    "pymemsim_mcp": {
      "command": "uvx",
      "args": ["pymemsim-mcp", "--mode", "stdio"]
    }
  }
}
```

## Expected MCP Server

The expected scientific MCP server is:

```text
pymemsim_mcp
```

Expected command:

```bash
uvx pymemsim-mcp --mode stdio
```

Expected tools may include:

- `simulate_gas_hfm`
- `hfm_feed_flow_rate_analyzer`
- `check_yaml_reference`

Tool names, schemas, accepted units, and required payload fields must always be discovered from the live MCP server before use. Local examples and historical notes are guidance, not the authoritative interface.

## Core Scientific Concepts

### `reference_content`

YAML-formatted thermodynamic reference content prepared for PyThermoDB and PyThermoLinkDB. This includes component constants, property tables, equations, coefficients, arguments, returns, units, metadata, and validity ranges when available.

### Conventional Inputs

Process and membrane inputs passed separately from `reference_content`, such as:

- components and feed composition;
- feed flow rate;
- feed and permeate pressure;
- temperature;
- hollow-fiber geometry;
- permeance or permeability;
- flow configuration;
- solver options.

### `model_source`

The internal runtime thermodynamic object built inside the MCP scientific application. Agents should not manually construct or expose it.

## Workflows

Use the workflow files before executing scientific work.

| Workflow | Use When |
| --- | --- |
| `workflows/membrane-simulation.md` | Running or preparing hollow-fiber membrane simulations. |
| `workflows/reference-content-generation.md` | Creating, repairing, or validating YAML thermodynamic `reference_content`. |
| `workflows/sensitivity-analysis.md` | Running multi-case studies over flow rate, pressure, temperature, composition, permeance, geometry, or solver settings. |

## Thermodynamic Reference Skill

The `pythermodb-reference-maker` skill is included for each supported harness. It converts thermodynamic tables, correlations, constants, matrix parameters, and source material into structured PyThermoDB-compatible YAML.

It supports:

- data tables;
- constants tables;
- matrix-parameter tables;
- equation tables;
- coefficient scaling;
- validity ranges;
- executable equation bodies using project notation;
- YAML validation scripts.

The skill must preserve source units and metadata. It must not guess coefficients, units, validity ranges, or missing scientific values.

## Example Cases

The `examples/` directory contains hollow-fiber membrane validation cases:

- `case-1.md`: CO2/CH4 co-current gas separation based on Tranchino et al. data.
- `case-2.md`: CO2/O2/N2 counter-current gas separation based on Rautenbach et al. data.
- `case-3.md`: O2/N2 co-current and counter-current air separation based on Feng et al. data.

The `examples/validation data/` directory contains CSV files with experimental validation points for comparison against deterministic simulation results.

## Prompt Templates

The `prompts/` directory contains starter prompts for constructing thermodynamic `reference_content`, including CO2/CH4 and O2/N2 reference-generation tasks.

These prompts are examples only. Agents must still follow `AGENTS.md`, the applicable workflow, the live MCP schema, and active MCP scientific requirement resources.

## Scientific Guardrails

Agents using this repository must follow these rules:

- Do not invent thermodynamic data, membrane parameters, units, validity ranges, or solver results.
- Do not claim validation or simulation succeeded unless the corresponding deterministic tool succeeded.
- Keep `reference_content` separate from conventional process and membrane inputs.
- Inspect live MCP schemas and scientific resources before preparing payloads.
- Validate `reference_content` separately from conventional inputs.
- Preserve source units; let the scientific application perform internal PyCUC conversion.
- Use deterministic PyMemSim-MCP tools for numerical results when available.
- Report assumptions, defaults, warnings, diagnostics, limitations, and reproducibility information.

## Typical Agent Workflow

1. Classify the user request: explanation, input preparation, validation, simulation execution, sensitivity analysis, or code modification.
2. Read the relevant workflow in `workflows/`.
3. Discover the live MCP server, tools, schemas, and scientific requirement resources.
4. Identify required components, thermodynamic properties, conventional inputs, and solver options.
5. Prepare or validate `reference_content` using `pythermodb-reference-maker` when needed.
6. Validate conventional inputs against the live tool schema.
7. Execute the deterministic MCP tool only after validation passes.
8. Review convergence status, warnings, physical bounds, and mass-balance diagnostics when available.
9. Report results with enough information to reproduce the run.

## Installation Notes

This repository assumes the scientific execution stack is installed or available through the MCP command:

```bash
uvx pymemsim-mcp --mode stdio
```

Depending on the harness, configure the MCP server using:

- `.codex/config.toml` for Codex;
- `.gemini/settings.json` for Gemini;
- the equivalent MCP configuration mechanism for Claude or other harnesses.

The repository itself is primarily configuration, prompts, workflows, examples, and agent skills. It does not require a local Python package install unless you are running the included skill validation scripts or the external MCP server locally.

## Status

This repo is an AI-agent orchestration layer for membrane simulation workflows. Numerical truth should come from PyMemSim-MCP and its underlying scientific packages, not from free-form LLM calculation.

## ❓ FAQ

For any questions, contact me on [LinkedIn](https://www.linkedin.com/in/sina-gilassi/).

## 📄 License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.

## 👨‍💻 Authors

- [@sinagilassi](https://www.github.com/sinagilassi)