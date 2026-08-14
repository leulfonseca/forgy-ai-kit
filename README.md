# Forgy AI Kit

![Forgy AI Kit conecta Codex e Claude Code a um contexto compartilhado](assets/forgy-ai-kit-social.png)

Contexto portátil para alternar entre Codex e Claude Code sem recomeçar o projeto do zero.

Criado por Leonardo Fonseca, na Forgy Digital.

[Landing e guia](https://forgy-ai-kit.vercel.app) · [Release mais recente](https://github.com/leulfonseca/forgy-ai-kit/releases/latest)

## O problema que o kit resolve

Codex e Claude Code possuem mecanismos próprios de instruções, chats e memória. Sem uma camada compartilhada, decisões importantes ficam presas em uma ferramenta ou em uma conversa antiga.

O Forgy AI Kit cria uma fonte de verdade versionada dentro de cada projeto:

```text
projeto/
├── AGENTS.md
├── CLAUDE.md
└── docs/ai-context/
    ├── README.md
    ├── ARCHITECTURE.md
    ├── INVARIANTS.md
    ├── CHANGE_PROTOCOL.md
    ├── DECISIONS.md
    ├── CURRENT_WORK.md
    └── MEMORY_MIGRATION.md
```

Assim, você pode trabalhar com Claude Code, fechar a ferramenta e continuar no Codex — ou fazer o caminho inverso — mantendo arquitetura, decisões, invariantes e trabalho ativo acessíveis aos dois agentes.

## Instalação

Requisito: Node.js 18 ou superior.

Instalação guiada (Windows, macOS ou Linux):

```bash
npx --yes https://github.com/leulfonseca/forgy-ai-kit/releases/download/v0.3.0/forgy-ai-kit-0.3.0.tgz install
```

O assistente pergunta onde guardar o kit, quais agentes configurar e pede confirmação antes de alterar arquivos. Para automações, CI ou instalação sem perguntas, informe as opções explicitamente:

```bash
npx --yes https://github.com/leulfonseca/forgy-ai-kit/releases/download/v0.3.0/forgy-ai-kit-0.3.0.tgz install --kit-dir "/caminho/escolhido/forgy-ai-kit" --agents codex,claude --non-interactive
```

O instalador preserva instruções e hooks globais existentes, gerencia somente os próprios blocos/handlers e cria backups antes de substituir itens controlados pelo kit.

## Uso automático em cada projeto

A versão 0.3 registra o mesmo detector somente leitura nos hooks `SessionStart` do Codex e do Claude Code. Ao abrir um agente dentro de uma raiz Git, ele informa um destes estados:

- `READY`: o contexto compartilhado está completo;
- `MIGRATE_REQUIRED`: existe contexto do Claude que precisa ser promovido com segurança;
- `INIT_REQUIRED`: ainda faltam os arquivos base do projeto;
- `NO_GIT_PROJECT`: a pasta não é um projeto Git e não será inicializada por engano.

O hook nunca grava no repositório. Quando você pede uma feature ou correção, os adapters orientam o agente a executar automaticamente a skill adequada antes da mudança. Você não precisa mais colar um prompt especial em cada chat.

Na primeira execução:

- no Codex, abra `/hooks`, revise o handler salvo em `~/.codex/hooks.json` e confie na definição;
- no Claude Code, aceite a confiança do workspace quando solicitado; o handler fica em `~/.claude/settings.json`.

Para conferir o estado sem gravar:

```bash
npx --yes https://github.com/leulfonseca/forgy-ai-kit/releases/download/v0.3.0/forgy-ai-kit-0.3.0.tgz inspect --project-dir "/caminho/do/projeto"
```

## Inicialização manual opcional

```bash
npx --yes https://github.com/leulfonseca/forgy-ai-kit/releases/download/v0.3.0/forgy-ai-kit-0.3.0.tgz init --project-dir "/caminho/do/projeto"
```

O comando cria somente os arquivos ausentes e continua disponível para CI ou preparação explícita.

## Diagnóstico

```bash
npx --yes https://github.com/leulfonseca/forgy-ai-kit/releases/download/v0.3.0/forgy-ai-kit-0.3.0.tgz doctor --kit-dir "/pasta/escolhida" --agents codex,claude
```

Se você aceitou `~/.forgy-ai-kit`, `--kit-dir` pode ser omitido. Para remover somente a automação e preservar adapters, skills e todos os outros hooks:

```bash
npx --yes https://github.com/leulfonseca/forgy-ai-kit/releases/download/v0.3.0/forgy-ai-kit-0.3.0.tgz hooks remove --agents codex,claude
```

## O que é compartilhado

- arquitetura e limites do sistema;
- invariantes que não podem ser quebrados;
- decisões técnicas e suas razões;
- protocolo de mudança e validação;
- trabalho ativo e próximos passos;
- skills de migração e segurança;
- fatos históricos promovidos após verificação.

## O que não é copiado automaticamente

- chats completos;
- auto memory nativa do Claude Code ou memória local do Codex;
- tokens, credenciais e arquivos `.env`;
- permissões históricas para push, deploy ou produção;
- lembranças não verificadas no código atual.

Memória nativa continua útil para recordação. Regras obrigatórias e conhecimento necessário para não quebrar o projeto pertencem ao repositório versionado.

## Integridade e privacidade

Cada release inclui o pacote `.tgz` e seu checksum SHA-256. Confira o checksum antes de executar o artefato em ambientes sensíveis.

O repositório público contém documentação e releases de distribuição. O ambiente de desenvolvimento, os testes internos e o histórico de construção não são necessários para instalar o kit.

Consulte [SECURITY.md](SECURITY.md) para reportar vulnerabilidades.

## Status

A série `0.3.x` é uma versão inicial. O formato do contexto e os comandos já são versionados, mas a política de licenciamento definitiva será definida antes de uma versão estável.
