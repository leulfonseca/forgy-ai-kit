# Segurança

## Versões suportadas

Somente a release mais recente da série `0.3.x` recebe correções durante a fase inicial.

## Verificação do artefato

Cada release publica um arquivo `.sha256` ao lado do pacote `.tgz`. Compare o SHA-256 do arquivo baixado antes de executá-lo em ambientes sensíveis.

## Dados que o instalador não coleta

O Forgy AI Kit não possui telemetria nem backend em runtime. O instalador não envia chats, memórias, código dos projetos, tokens ou credenciais.

O hook `SessionStart` faz apenas inspeção local de nomes de arquivos conhecidos e da raiz Git. Ele não lê `.env`, não copia memória e não altera projetos. Antes de registrar o handler, o instalador preserva a configuração existente e cria backup quando houver gravação.

## Reportar uma vulnerabilidade

Use a opção privada **Report a vulnerability** na aba Security deste repositório. Não publique segredos, tokens, caminhos pessoais ou detalhes exploráveis em uma issue pública.
