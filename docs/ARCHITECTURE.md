# Arquitetura de distribuição

## Camadas

1. **Landing na Vercel:** orientação, comandos e acesso ao download.
2. **Repositório público:** documentação, changelog, segurança e histórico de releases.
3. **Release versionada:** runtime mínimo necessário para instalar adapters, skills e templates.
4. **Contexto de cada projeto:** `AGENTS.md`, `CLAUDE.md` e `docs/ai-context/` versionados junto ao código do usuário.
5. **Memória local dos agentes:** evidência auxiliar, nunca a única autoridade de uma regra obrigatória.

## Fluxo entre agentes

Claude Code e Codex leem adapters próprios, mas ambos apontam para o mesmo contexto versionado. Ao trocar de ferramenta, o novo agente reconstrói o estado atual a partir do repositório, em vez de depender do chat anterior.

O kit não tenta unificar bancos privados de auto memory. Conhecimento durável é promovido para arquivos compartilhados somente depois de ser verificado contra código, testes e configuração atuais.
