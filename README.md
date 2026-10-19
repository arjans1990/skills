# ABC — Arjan's Blueprint Companion

*Think critically. Challenge assumptions. Design simply.*

I created ABC to bring my approach to architectural reasoning into your AI coding agent. Use it as a sparring partner to sharpen a proposal, challenge assumptions, and work toward a simple design its owners can understand and maintain.

It supports data, infrastructure, AI, integration, and solution architecture decisions across organizations and technology stacks.

## What it helps with

- Clarify the problem and the outcome before choosing a solution.
- Find shared mechanisms and distinguish differences that justify separate designs.
- Make responsibilities, correctness conditions, and operational tradeoffs explicit.
- Explore simpler alternatives using existing capabilities.
- Converge on a defensible recommendation, including its remaining tradeoffs.

ABC asks one substantive question at a time, responds in your language, and answers narrow implementation questions directly. It accepts justified complexity and stops when the decision is sufficiently clear.

## Install

Run this command with Node.js/npm available:

```sh
npx skills@latest add arjans1990/skills --skill abc-arjans-blueprint-companion
```

Select your agent during installation and follow the prompts. See the [skills CLI documentation](https://github.com/vercel-labs/skills) for supported agents and installation options.

## Get started

Ask your agent to use ABC and share the problem, your proposal, and the relevant constraints:

```text
Use abc-arjans-blueprint-companion to review this proposal:
we want a separate pipeline for each domain. Help us determine
which differences justify separation and what we could share.
```

You can bring an architecture proposal, a recurring incident, or a decision between competing approaches. Provide relevant project context and evidence so the discussion can focus on the choices that matter. A short recommendation is usually enough; ask for an architecture decision record when you need one.

## About

ABC is a portable [Agent Skill](https://agentskills.io) inspired by my architectural reasoning: understand the problem, challenge unnecessary complexity, and make deliberate tradeoffs. These principles guide judgment and leave room for context and exceptions.

The complete skill lives in [skills/abc-arjans-blueprint-companion](skills/abc-arjans-blueprint-companion). It requires no additional skill or custom agent persona.

## Make it your own

This skill reflects my personal views on architecture, shaped by years of experience. You are welcome to fork it and adapt it to your own perspective and way of working.

## License

[MIT](LICENSE).
