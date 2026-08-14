# Changelog

Todas as mudanças relevantes da distribuição são registradas neste arquivo.

## 0.3.0 - 2026-08-14

- detector somente leitura que encontra a raiz Git e classifica o contexto como `READY`, `MIGRATE_REQUIRED`, `INIT_REQUIRED` ou `NO_GIT_PROJECT`;
- hooks globais `SessionStart` para Codex e Claude Code usando o mesmo runtime portátil;
- merge idempotente que preserva configurações e hooks existentes com backup anterior;
- comando `inspect` para diagnóstico manual e `hooks remove` para remoção seletiva;
- adapters e skill de bootstrap atualizados para agir automaticamente em demandas materiais;
- tutorial da landing atualizado com confiança inicial, estados e fluxo sem prompts repetidos.

## 0.2.0 - 2026-08-14

- assistente interativo para escolher a pasta canônica, os agentes e confirmar a instalação;
- modo `--non-interactive` para automações, CI e comandos previamente configurados;
- gerador de comando na landing com opções para Windows, macOS/Linux, Codex e Claude Code;
- fallback compatível para copiar comandos em navegadores sem Clipboard API;
- validação conjunta da versão, nome, tamanho e SHA-256 do artefato publicado.

## 0.1.0 - 2026-08-14

- instalador multiplataforma executável com Node.js 18+;
- adapters globais para Codex e Claude Code;
- skills compartilhadas de bootstrap e segurança de mudanças;
- migração de projetos iniciados no Claude Code;
- templates versionados para `AGENTS.md`, `CLAUDE.md` e `docs/ai-context/`;
- instalação idempotente com preservação e backup;
- diagnóstico de configuração para ambos os agentes;
- distribuição por pacote versionado com checksum SHA-256.
