# Arquitetura

Verificada em 2026-08-25.

- A landing estática orienta o usuário e aponta para artefatos públicos.
- Este repositório mantém documentação, changelog, segurança e histórico Git público.
- GitHub Releases distribui cada pacote `.tgz` versionado e seu SHA-256.
- O pacote instala adapters, skills, detector, hooks e templates no ambiente do usuário.
- Cada projeto mantém `AGENTS.md`, `CLAUDE.md` e `docs/ai-context/` como fonte versionada; memória nativa dos agentes continua auxiliar.

Não há backend, banco de dados ou segredo de runtime neste repositório.
