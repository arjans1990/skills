# Arjan the Architect

A portable Agent Skill for constructive architecture sparring: challenge the problem framing, find shared mechanisms and control points, and converge on a simple solution its owners can maintain.

Inspired by Arjan's architectural reasoning principles. This is not a simulation of Arjan or a claim of his endorsement. It works across organizations and stacks without private conversations, internal materials, or another skill.

## Install

Requires an Agent Skills-compatible client. The CLI route also requires Node.js/npm and access to the source repository. From the project where you want to use it:

```sh
npx skills@latest add arjans1990/skills --skill arjan-the-architect --agent github-copilot
```

Add `--global` for personal installation across projects. Use `--copy` if symlinks are unsuitable, including on Windows. To inspect discovery without installing:

```sh
npx skills@latest add arjans1990/skills --list
```

These GitHub commands require this version to have been pushed to that remote; creating these files locally does not publish them. To try the current checkout, replace `arjans1990/skills` with its absolute local path, or run this from the checkout:

```sh
npx skills@latest add . --skill arjan-the-architect --agent github-copilot
```

For other agents, omit `--agent github-copilot` and select your installed client interactively. The distributable is the entire [skills/arjan-the-architect](skills/arjan-the-architect) directory. No scripts, vendor extensions, or custom agent persona are required at runtime.

### VS Code / GitHub Copilot

The CLI currently targets `.agents/skills/` for a project and `~/.copilot/skills/` for personal Copilot skills. Alternatively, copy the complete skill directory to `.github/skills/arjan-the-architect/` in the target project; preserve its references. Avoid installing duplicate copies through multiple paths.

Open Copilot Chat and invoke `/arjan-the-architect`, or ask for an architecture review. Use `/skills` to inspect available skills if discovery fails. Relevant requests can also activate it automatically; discovery does not guarantee activation for every prompt. No explicit-only policy is set.

Other compatible clients have their own discovery paths and invocation syntax. Copy the full directory into their documented skill location and invoke it by name; the standard format alone does not prove end-to-end client compatibility.

## Use

```text
/arjan-the-architect We propose a separate pipeline for each domain.
Help us test whether the differences justify that design.
```

```text
Review this proposal using Arjan the Architect. We want a new AI agent
to route requests. The existing routing rules and constraints are attached.
```

Supply the problem, proposal, and available constraints. The skill reads relevant accessible project context, then asks one substantive question at a time. It distinguishes evidence from assumptions, accepts justified complexity, and stops when the decision is sound. It responds in your language and answers narrow implementation questions directly. An ADR is optional.

Examples are explicitly generalized or synthetic. They do not establish historical outcomes or organizational standards. Do not add confidential project material to the published skill; provide appropriate redacted runtime context instead.

## Updates

For CLI-managed installations:

```sh
npx skills@latest update arjan-the-architect
```

Select the intended installation scope when prompted. Review upstream changes before adopting them, especially if you customized a copy. For manual installations, replace the whole directory from a reviewed revision, retaining local customization separately.

## Validation and evaluation

Run format validation using the Agent Skills reference implementation (requires `uv` and network access on first run):

```sh
uvx --from skills-ref agentskills validate skills/arjan-the-architect
```

The specification currently shows the executable as `skills-ref`; the package resolved during validation exposes `agentskills` instead. Run the prompts and score conversations with [the evaluation guide](evaluations/README.md) and [scenarios](evaluations/scenarios.md). Format validation does not establish behavioral quality. The evaluation guide summarizes recorded results and known limitations.

## Sources and open decisions

The format, commands, discovery paths, and invocation guidance were checked on 2026-10-16 against the [Agent Skills specification](https://agentskills.io/specification), [skills CLI documentation](https://github.com/vercel-labs/skills), and [VS Code documentation](https://code.visualstudio.com/docs/agent-customization/agent-skills). CLI versions and client behavior can change. The CLI discovers `skills/<name>/SKILL.md`; VS Code requires installation into a supported discovery path.

MVP defaults are constructive challenge, automatic discovery, bounded inspection, and optional decision records. Automatic discovery is a reversible product choice; a separate custom agent persona remains optional future work, not a dependency. Contributions should follow [AGENTS.md](AGENTS.md).

Historical transcripts and measured case outcomes are unavailable; examples are generalized or synthetic, and principles are not independently verified personal quotations. Additional real case details require supporting evidence and authorization to publish. No external skill content has been copied; source and license review is required before any future reuse. Client compatibility and evaluation thresholds still need validation as described in the evaluation guide.

Licensed under the existing [MIT license](LICENSE). No upstream grilling skill text or files have been copied.
