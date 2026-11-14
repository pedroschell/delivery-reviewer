# delivery-reviewer

[Português](README.md) | **English**

A Claude Code subagent that **reviews an implementation that has already been delivered** and returns an executive summary: what was done, the stack used, a quality score, the issues found, and the next step.

After a long feature, it's hard to remember offhand what changed and whether it turned out well. This agent reads the changed files with an outside eye and always answers in the same format, in about 300 words, so any developer can understand the state of the delivery in a minute.

## The response format

The agent's prompt is written in Portuguese, so it replies with these Portuguese headings:

```
## Implementado
## Stack identificada
## Arquivos principais
## Qualidade Geral        (score from 0 to 10 and the reason in two sentences)
## Problemas encontrados
## Melhorias futuras
## Próximo passo recomendado
```

## Why it doesn't fix anything

The agent only has read and execution tools (`Read`, `Grep`, `Glob`, `Bash`), and its rules forbid changing code or creating files. The reviewer shouldn't be the one who fixes things: this keeps the evaluation separate from the implementation, and you decide what to do about each issue.

## How to install

For all your projects:

```bash
mkdir -p ~/.claude/agents
curl -o ~/.claude/agents/delivery-reviewer.md https://raw.githubusercontent.com/pedroschell/delivery-reviewer/main/delivery-reviewer.md
```

Or for a single project, by saving the file to `.claude/agents/delivery-reviewer.md` inside it.

After finishing a task, ask *"run the delivery-reviewer on this delivery"*.

## Works well with

The [orchestrator](https://github.com/pedroschell/orchestrator), which plans the task before you start. The orchestrator plans, the delivery-reviewer checks.

## License

MIT
