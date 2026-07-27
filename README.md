# Escala Equipe 9132 — versão 2.1

Aplicativo PWA para consulta da escala fixa e fechamento de cargas, com sincronização pelo Google Sheets.

## Alterações
- Removido o botão Relatórios e todas as funções associadas.
- Removida a seleção de mês da tela principal e da administração.
- Mantido somente o seletor de turno na parte superior.
- A escala usa sempre os dias 01 a 31, independentemente do mês.
- Removida a função de copiar escala para outro mês.
- O Apps Script migra automaticamente a escala mais recente para a referência fixa `FIXA`.

Substitua o Apps Script, execute `configurarSistema`, publique uma nova versão da implantação e depois substitua os arquivos no GitHub.
