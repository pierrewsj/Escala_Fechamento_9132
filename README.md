# Escala Equipe 9132 — versão 2.2

Aplicativo web para consulta da escala fixa, fechamento de cargas e montagem de escala especial de sábado para hora extra.

## Novidade: Escala de sábado — HE

Na área Admin é possível:

- escolher uma data que seja sábado;
- montar uma escala separada por turno;
- selecionar somente os colaboradores que farão hora extra;
- definir posto e observação de cada participante;
- copiar o sábado anterior;
- usar como sugestão os postos da escala fixa do mesmo dia do mês;
- salvar como rascunho ou publicar;
- receber alerta de colaborador sem posto e possível duplicidade de posto.

Na tela principal, o botão **Sábado HE** mostra a escala publicada do próximo sábado. Quando o dia atual for sábado, o botão **Hoje** mostra automaticamente a escala especial publicada.

A função `configurarSistema()` do Apps Script cria a aba `Escala_Sabado_HE` sem apagar as abas existentes.

## Atualização

1. Substitua o código do Apps Script pelo conteúdo de `apps-script-atualizado.txt`.
2. Execute `configurarSistema()` uma vez e autorize o acesso.
3. Crie uma nova versão da implantação do Web App.
4. Substitua no GitHub os arquivos do aplicativo pelos arquivos desta pasta.
5. Aguarde o GitHub Pages publicar a nova versão.
