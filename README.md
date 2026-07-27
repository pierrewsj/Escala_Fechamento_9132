# Escala Equipe 9132 — versão 2.0

Aplicativo PWA para consulta da escala, fechamento e relatório de cargas, com sincronização pelo Google Sheets.

## O que foi atualizado

- Mês e ano dinâmicos.
- Escala, colaboradores e postos preparados para sincronização centralizada.
- Senha administrativa validada por hash SHA-256; a senha inicial continua `4321`.
- Bloqueio temporário após cinco tentativas incorretas.
- Registro do colaborador preenchido automaticamente após ser cadastrado ou usado no primeiro fechamento.
- Histórico local dos lançamentos e aba **Relatórios**.
- Total por período, colaborador, turno e setor, com exportação CSV e impressão/PDF.
- Proteção no Apps Script contra protocolo duplicado.
- Fila offline: lançamentos sem internet são enviados quando a conexão volta.
- Toasts, animações, spinner de salvamento e foco acessível.
- PWA com estratégia de cache `stale-while-revalidate` e aviso de nova versão.
- Administração de colaboradores, postos, substituições, situações e cópia de mês.
- Aviso de possíveis duplicidades de posto no mesmo turno e dia.

## 1. Atualizar o Apps Script

1. Abra a planilha usada pelo aplicativo.
2. Acesse **Extensões > Apps Script**.
3. Apague o código antigo.
4. Copie todo o conteúdo de `apps-script-atualizado.txt` ou `apps-script.gs`.
5. Clique em **Salvar**.
6. No seletor de funções, escolha `configurarSistema` e clique em **Executar** uma vez.
7. Autorize o acesso solicitado pelo Google.
8. Vá em **Implantar > Gerenciar implantações**.
9. Edite a implantação existente, escolha **Nova versão** e clique em **Implantar**.
10. Mantenha o acesso como **Qualquer pessoa**.

Ao atualizar a implantação existente, o endereço do Web App normalmente continua o mesmo e já está configurado no arquivo `config.js`.

O código cria automaticamente as abas:

- `Config`
- `Colaboradores`
- `Postos`
- `Escala`
- `Fechamento`
- `Substituicoes`
- `Historico`

Os dados existentes da aba `Fechamento` são preservados. O novo código acrescenta colunas de controle quando necessário.

## 2. Publicar no GitHub Pages

Substitua no repositório todos os arquivos antigos pelos arquivos desta pasta. Não envie o arquivo ZIP para dentro do repositório; envie os arquivos extraídos.

Depois:

1. Abra **Settings > Pages**.
2. Confirme **Deploy from a branch**.
3. Selecione a branch `main` e a pasta `/root`.
4. Aguarde a publicação.

O navegador pode levar alguns segundos para reconhecer a nova versão. Quando o aplicativo detectar a atualização, mostrará o botão **Atualizar agora**.

## Senha administrativa

A senha inicial é `4321`.

Para trocar a senha sem deixá-la no código público:

1. Abra o Apps Script.
2. No seletor de funções, escolha `definirSenhaAdmin`.
3. Como essa função recebe um parâmetro, execute pelo editor com uma função temporária:

```javascript
function trocarMinhaSenha() {
  definirSenhaAdmin('SUA_NOVA_SENHA');
}
```

4. Execute `trocarMinhaSenha` uma vez e depois apague essa função temporária.
5. Para usar uma nova senha também na verificação local do aplicativo, gere o SHA-256 dela e substitua as duas partes de `adminHashPartes` no arquivo `config.js`.

## Observação sobre a sincronização

Os envios são feitos para o Web App do Apps Script. Em caso de falta de internet, o aparelho mantém uma fila local e tenta enviar novamente quando a conexão retornar. O Google Sheets continua sendo a fonte central dos dados quando está acessível.
