# Instalação da skill faststore-dev

Instale a **pasta inteira** `faststore-dev`, com `SKILL.md` e `references/`. Os caminhos abaixo são para agentes de programação que aceitam Agent Skills; escolher um modelo de LLM no chat, por si só, não instala a skill.

Ao receber este pacote por um repositório ou arquivo compactado, coloque a pasta `faststore-dev` em um dos destinos abaixo. A skill não inclui código de loja: ao usá-la, o agente lê o projeto aberto para descobrir sua versão, organização e convenções.

| Ferramenta  | Para todos os seus projetos       | Apenas para um projeto                    | Documentação                                                 |
| ----------- | --------------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Codex       | `~/.agents/skills/faststore-dev/` | `<projeto>/.agents/skills/faststore-dev/` | [OpenAI](https://learn.chatgpt.com/docs/build-skills)        |
| Claude Code | `~/.claude/skills/faststore-dev/` | `<projeto>/.claude/skills/faststore-dev/` | [Anthropic](https://code.claude.com/docs/en/skills)          |
| Gemini CLI  | `~/.gemini/skills/faststore-dev/` | `<projeto>/.gemini/skills/faststore-dev/` | [Google](https://geminicli.com/docs/cli/using-agent-skills/) |
| Cursor      | `~/.cursor/skills/faststore-dev/` | `<projeto>/.cursor/skills/faststore-dev/` | [Cursor](https://cursor.com/help/customization/skills)       |

`~` representa a pasta do usuário. No Windows, é o valor de `$env:USERPROFILE`. Escolha **um** local por ferramenta para evitar cópias com o mesmo nome. Codex, Gemini CLI e Cursor também reconhecem `.agents/skills/`, útil para compartilhar uma instalação por projeto; Claude Code usa `.claude/skills/`.

O caminho de Claude Code é para a ferramenta local; o chat do Claude na web não lê automaticamente as pastas do seu computador.

## Exemplo no Windows: instalação pessoal no Codex

Abra PowerShell na pasta que contém `faststore-dev` e execute, para uma primeira instalação:

```powershell
$skillsRoot = Join-Path $env:USERPROFILE '.agents\skills'
New-Item -ItemType Directory -Force -Path $skillsRoot | Out-Null
Copy-Item -LiteralPath '.\faststore-dev' -Destination $skillsRoot -Recurse
```

Para Claude Code, Gemini CLI ou Cursor, troque apenas o valor de `$skillsRoot` por `.claude\skills`, `.gemini\skills` ou `.cursor\skills`. Para instalar no projeto, copie a pasta para o caminho da coluna “Apenas para um projeto”. Ao atualizar uma instalação existente, substitua os arquivos **dentro** de `faststore-dev`; não crie uma pasta `faststore-dev/faststore-dev`.

No macOS ou Linux, para instalar no Codex a partir da pasta que contém `faststore-dev`:

```sh
mkdir -p ~/.agents/skills
cp -R faststore-dev ~/.agents/skills/
```

Para as outras ferramentas, use o destino correspondente da tabela. Ao atualizar a skill, substitua a cópia existente mantendo uma única pasta `faststore-dev` no destino.

Confirme que o destino contém `faststore-dev/SKILL.md` e `faststore-dev/references/`. Depois, peça uma tarefa de FastStore ou invoque a skill: `$faststore-dev` no Codex, `/faststore-dev` no Claude Code ou Cursor. No Gemini CLI, use `/skills list` para conferir a descoberta e mencione `faststore-dev` no pedido. Se a skill não aparecer, reinicie Codex ou Claude Code; no Gemini CLI, use `/skills reload`.
