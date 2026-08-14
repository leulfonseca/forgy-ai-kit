# Changelog

Todas as mudanças relevantes da distribuição são registradas neste arquivo.

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
