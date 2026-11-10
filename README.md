# qa

Um subagente para o Claude Code que **revisa uma implementação já entregue** e devolve um resumo executivo: o que foi feito, a stack usada, uma nota de qualidade, os problemas encontrados e o próximo passo.

Depois de uma feature longa, é difícil saber de cabeça o que mudou e se ficou bom. Este agente lê os arquivos alterados com um olhar de fora e responde sempre no mesmo formato, em cerca de 300 palavras, para qualquer desenvolvedor entender o estado da entrega em um minuto.

## O formato da resposta

```
## Implementado
## Stack identificada
## Arquivos principais
## Qualidade Geral        (nota de 0 a 10 e o motivo em duas frases)
## Problemas encontrados
## Melhorias futuras
## Próximo passo recomendado
```

## Por que ele não corrige nada

O agente só tem ferramentas de leitura e execução (`Read`, `Grep`, `Glob`, `Bash`) e as regras proíbem alterar código ou criar arquivos. Quem revisa não deve ser quem corrige: assim a avaliação fica separada da implementação, e você decide o que fazer com cada problema.

## Como instalar

Para todos os seus projetos:

```bash
mkdir -p ~/.claude/agents
curl -o ~/.claude/agents/qa.md https://raw.githubusercontent.com/pedroschell/qa/main/qa.md
```

Ou só para um projeto, salvando o arquivo em `.claude/agents/qa.md` dentro dele.

Depois de terminar uma tarefa, peça *"roda o qa nessa entrega"*.

## Combina com

O [orchestrator](https://github.com/pedroschell/orchestrator), que planeja a tarefa antes de começar. O orchestrator planeja, o qa confere.

## Licença

MIT
