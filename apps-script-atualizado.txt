const VERSAO_API = '2.0.0';
const EQUIPE_PADRAO = '9132';
const HASH_ADMIN_PADRAO = 'fe2592b42a727e977f055947385b709cc82b16b9a87f88c6abf3900d65d0cdc3';
const PROPRIEDADE_HASH_ADMIN = 'ESCALA_9132_ADMIN_HASH';

const NOMES_ABAS = Object.freeze({
  config: 'Config',
  colaboradores: 'Colaboradores',
  postos: 'Postos',
  escala: 'Escala',
  fechamento: 'Fechamento',
  substituicoes: 'Substituicoes',
  historico: 'Historico'
});

const CABECALHOS = Object.freeze({
  config: ['Chave', 'Valor', 'Atualizado Em'],
  colaboradores: ['ID', 'Nome', 'Registro', 'Turno', 'Ativo', 'Atualizado Em'],
  postos: ['Código', 'Localização', 'Setor', 'Ativo', 'Atualizado Em'],
  escala: ['Mês', 'ID Colaborador', 'Nome', 'Registro', 'Turno']
    .concat(Array.from({ length: 31 }, (_, i) => `Dia ${String(i + 1).padStart(2, '0')}`))
    .concat(['Ativo', 'Atualizado Em']),
  fechamento: ['Data', 'Colaborador', 'Registro', 'Turno', 'Setor/Posto', 'Quantidade', 'Protocolo', 'Data Envio', 'Hora Envio', 'ID Colaborador', 'Data ISO', 'Criado Em'],
  substituicoes: ['ID', 'Mês', 'ID Origem', 'Nome Origem', 'ID Destino', 'Nome Destino', 'Dia Início', 'Criado Em'],
  historico: ['Data/Hora', 'Ação', 'Detalhes', 'Usuário']
});

const DADOS_INICIAIS = {"postos":{"69":{"local":"Pátio central","setor":"Carregamento"},"70":{"local":"Pátio central","setor":"Carregamento"},"71":{"local":"G89","setor":"Caixaria"},"72":{"local":"G04","setor":"JIT"},"73":{"local":"G04","setor":"JIT"},"74":{"local":"Pensilina","setor":"Pensilina"},"75":{"local":"Pensilina","setor":"Pensilina"},"76":{"local":"Pensilina","setor":"Pensilina"},"77":{"local":"Pensilina","setor":"Pensilina"},"CMP":{"local":"Pátio central","setor":"Carregamento"},"G38":{"local":"Ilha ecológica","setor":"Ilha ecológica"},"G15":{"local":"Pátio de sucatas","setor":"Pátio de sucatas"},"G76":{"local":"Galpão 76","setor":"Expedição vasilhame"},"66AU":{"local":"G9","setor":"FTP"},"INT-89":{"local":"Interni","setor":"Interni"},"FPT/CX":{"local":"G8 FPT","setor":"Caixaria"},"RÁDIO":{"local":"Central de Segurança","setor":"Disponível para demandas"},"Pens.":{"local":"Pensilina","setor":"Pensilina"},"Ilha":{"local":"Ilha ecológica","setor":"Ilha ecológica"},"FPT-CX":{"local":"G8 FPT","setor":"Caixaria"}},"escala":[{"nome":"VANDER","turno":"1º Turno","dias":["G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15","G15"],"registro":"","ativo":true},{"nome":"PIERRE","turno":"1º Turno","dias":["G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38","G38"],"registro":"","ativo":true},{"nome":"DANIEL","turno":"1º Turno","dias":["Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens."],"registro":"","ativo":true},{"nome":"POLIANA S.","turno":"1º Turno","dias":["Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens."],"registro":"","ativo":true},{"nome":"VIANA","turno":"1º Turno","dias":["71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71"],"registro":"","ativo":true},{"nome":"JULIANO","turno":"1º Turno","dias":["69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69"],"registro":"","ativo":true},{"nome":"AIMEN","turno":"1º Turno","dias":["72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72"],"registro":"","ativo":true},{"nome":"CARLOS","turno":"1º Turno","dias":["74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74"],"registro":"","ativo":true},{"nome":"GINALDO","turno":"1º Turno","dias":["INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89"],"registro":"","ativo":true},{"nome":"JAIR","turno":"1º Turno","dias":["77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77"],"registro":"","ativo":true},{"nome":"DORIEL","turno":"1º Turno","dias":["CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP"],"registro":"","ativo":true},{"nome":"POLIANA G.","turno":"1º Turno","dias":["73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73"],"registro":"","ativo":true},{"nome":"RENATO","turno":"1º Turno","dias":["66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU"],"registro":"","ativo":true},{"nome":"MAXILENE","turno":"1º Turno","dias":["70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70"],"registro":"","ativo":true},{"nome":"ADRIANA","turno":"1º Turno","dias":["75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75"],"registro":"","ativo":true},{"nome":"REGINALDO","turno":"1º Turno","dias":["76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76"],"registro":"","ativo":true},{"nome":"AMANDA","turno":"1º Turno","dias":["G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76"],"registro":"","ativo":true},{"nome":"FABIANA","turno":"1º Turno","dias":["RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO"],"registro":"","ativo":true},{"nome":"CINTIA","turno":"1º Turno","dias":["FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX","69","72","74","INT-89","77","CMP","73","66AU","70","75","71","76","G76","RÁDIO","FPT/CX"],"registro":"","ativo":true},{"nome":"RENATO","turno":"2º Turno","dias":["Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha","Ilha"],"registro":"","ativo":true},{"nome":"GERMANO","turno":"2º Turno","dias":["Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens."],"registro":"","ativo":true},{"nome":"JUNIOR","turno":"2º Turno","dias":["Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens.","Pens."],"registro":"","ativo":true},{"nome":"ROGERIO","turno":"2º Turno","dias":["INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76"],"registro":"","ativo":true},{"nome":"CLAYTON","turno":"2º Turno","dias":["69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77"],"registro":"","ativo":true},{"nome":"NOGUEIRA","turno":"2º Turno","dias":["FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75"],"registro":"","ativo":true},{"nome":"WELINGTON","turno":"2º Turno","dias":["72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70"],"registro":"","ativo":true},{"nome":"GIDEÃO","turno":"2º Turno","dias":["66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71"],"registro":"","ativo":true},{"nome":"HUDSON","turno":"2º Turno","dias":["74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73"],"registro":"","ativo":true},{"nome":"AROLDO","turno":"2º Turno","dias":["76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89"],"registro":"","ativo":true},{"nome":"JOSÉ","turno":"2º Turno","dias":["77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69"],"registro":"","ativo":true},{"nome":"CAMILO","turno":"2º Turno","dias":["75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX"],"registro":"","ativo":true},{"nome":"ERCI","turno":"2º Turno","dias":["70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72"],"registro":"","ativo":true},{"nome":"MARCOS","turno":"2º Turno","dias":["71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU"],"registro":"","ativo":true},{"nome":"LEONEL","turno":"2º Turno","dias":["73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74","INT-89","77","FPT-CX","70","66AU","73","76","69","75","72","71","74"],"registro":"","ativo":true}]};

function doGet(e) {
  try {
    garantirEstrutura_();
    const parametros = (e && e.parameter) || {};
    const acao = String(parametros.acao || 'status');
    let resposta;

    if (acao === 'bootstrap') {
      resposta = obterBootstrap_(parametros.mesAno || mesAtual_());
    } else if (acao === 'relatorio') {
      resposta = obterRelatorio_(parametros);
    } else {
      resposta = {
        sucesso: true,
        mensagem: 'API Escala Equipe 9132 ativa',
        versao: VERSAO_API,
        dataHora: new Date().toISOString()
      };
    }

    return responder_(resposta, parametros.callback);
  } catch (erro) {
    return responder_({ sucesso: false, mensagem: mensagemErro_(erro), versao: VERSAO_API }, e && e.parameter && e.parameter.callback);
  }
}

function doPost(e) {
  const lock = LockService.getScriptLock();
  try {
    lock.waitLock(20000);
    garantirEstrutura_();
    const dados = lerCorpo_(e);
    const acao = String(dados.acao || 'salvarFechamento');
    let resposta;

    if (acao === 'salvarFechamento') {
      resposta = salvarFechamento_(dados);
    } else {
      validarAdmin_(dados.senha);
      switch (acao) {
        case 'salvarColaborador': resposta = salvarColaborador_(dados); break;
        case 'excluirColaborador': resposta = excluirColaborador_(dados); break;
        case 'salvarPosto': resposta = salvarPosto_(dados); break;
        case 'excluirPosto': resposta = excluirPosto_(dados); break;
        case 'salvarEscala': resposta = salvarEscala_(dados); break;
        case 'substituirColaborador': resposta = substituirColaborador_(dados); break;
        case 'copiarMes': resposta = copiarMes_(dados); break;
        case 'sincronizarTudo': resposta = sincronizarTudo_(dados); break;
        default: throw new Error(`Ação desconhecida: ${acao}`);
      }
    }

    SpreadsheetApp.flush();
    return responder_(resposta);
  } catch (erro) {
    return responder_({ sucesso: false, mensagem: mensagemErro_(erro), versao: VERSAO_API });
  } finally {
    try { lock.releaseLock(); } catch (_) { /* lock não adquirido */ }
  }
}

/** Execute manualmente apenas se desejar preparar a planilha antes do primeiro acesso. */
function configurarSistema() {
  garantirEstrutura_();
  return 'Sistema configurado com sucesso.';
}

/** Execute manualmente para trocar a senha administrativa. */
function definirSenhaAdmin(novaSenha) {
  if (!novaSenha || String(novaSenha).length < 4) throw new Error('A nova senha deve ter pelo menos 4 caracteres.');
  PropertiesService.getScriptProperties().setProperty(PROPRIEDADE_HASH_ADMIN, sha256_(String(novaSenha)));
  registrarHistorico_('ALTERAR SENHA', 'Senha administrativa alterada.', 'Administrador');
  return 'Senha alterada com sucesso.';
}

function garantirEstrutura_() {
  const planilha = SpreadsheetApp.getActiveSpreadsheet();
  prepararAba_(planilha, NOMES_ABAS.config, CABECALHOS.config);
  prepararAba_(planilha, NOMES_ABAS.colaboradores, CABECALHOS.colaboradores);
  prepararAba_(planilha, NOMES_ABAS.postos, CABECALHOS.postos);
  prepararAba_(planilha, NOMES_ABAS.escala, CABECALHOS.escala);
  prepararAba_(planilha, NOMES_ABAS.fechamento, CABECALHOS.fechamento);
  prepararAba_(planilha, NOMES_ABAS.substituicoes, CABECALHOS.substituicoes);
  prepararAba_(planilha, NOMES_ABAS.historico, CABECALHOS.historico);

  const propriedades = PropertiesService.getScriptProperties();
  if (!propriedades.getProperty(PROPRIEDADE_HASH_ADMIN)) propriedades.setProperty(PROPRIEDADE_HASH_ADMIN, HASH_ADMIN_PADRAO);

  const abaColaboradores = planilha.getSheetByName(NOMES_ABAS.colaboradores);
  const abaPostos = planilha.getSheetByName(NOMES_ABAS.postos);
  if (abaColaboradores.getLastRow() <= 1 && abaPostos.getLastRow() <= 1) popularDadosIniciais_();
}

function prepararAba_(planilha, nome, cabecalhos) {
  let aba = planilha.getSheetByName(nome);
  if (!aba) aba = planilha.insertSheet(nome);

  if (aba.getMaxColumns() < cabecalhos.length) {
    aba.insertColumnsAfter(aba.getMaxColumns(), cabecalhos.length - aba.getMaxColumns());
  }

  const primeiraLinha = aba.getRange(1, 1, 1, cabecalhos.length).getValues()[0];
  const vazia = primeiraLinha.every(valor => valor === '');
  const pareceCabecalho = String(primeiraLinha[0] || '').toLowerCase() === String(cabecalhos[0]).toLowerCase();
  if (vazia || pareceCabecalho || aba.getLastRow() === 0) {
    aba.getRange(1, 1, 1, cabecalhos.length).setValues([cabecalhos]);
  } else {
    // Se a primeira linha já contém dados, cria o cabeçalho sem apagar nenhum registro.
    aba.insertRowBefore(1);
    aba.getRange(1, 1, 1, cabecalhos.length).setValues([cabecalhos]);
  }

  const cabecalho = aba.getRange(1, 1, 1, cabecalhos.length);
  cabecalho
    .setFontWeight('bold')
    .setFontColor('#06111d')
    .setBackground('#22d3ee')
    .setHorizontalAlignment('center');
  aba.setFrozenRows(1);
  aba.getDataRange().setVerticalAlignment('middle');
  if (nome === NOMES_ABAS.fechamento) {
    aba.setColumnWidth(1, 95);
    aba.setColumnWidth(2, 170);
    aba.setColumnWidth(5, 240);
    aba.setColumnWidth(7, 220);
  }
}

function popularDadosIniciais_() {
  const planilha = SpreadsheetApp.getActiveSpreadsheet();
  const agora = new Date();
  const mes = mesAtual_();
  const postos = DADOS_INICIAIS.postos || {};
  const escala = DADOS_INICIAIS.escala || [];

  const linhasPostos = Object.keys(postos).map(codigo => [
    codigo,
    postos[codigo].local || postos[codigo].setor || codigo,
    postos[codigo].setor || postos[codigo].local || codigo,
    true,
    agora
  ]);
  if (linhasPostos.length) planilha.getSheetByName(NOMES_ABAS.postos).getRange(2, 1, linhasPostos.length, CABECALHOS.postos.length).setValues(linhasPostos);

  const usados = {};
  const linhasColaboradores = [];
  const linhasEscala = [];
  escala.forEach((pessoa, indice) => {
    let base = `${slug_(pessoa.nome)}-${slug_(pessoa.turno || 'turno')}` || `colaborador-${indice + 1}`;
    let id = base;
    let contador = 2;
    while (usados[id]) id = `${base}-${contador++}`;
    usados[id] = true;
    const dias = Array.from({ length: 31 }, (_, i) => pessoa.dias && pessoa.dias[i] || '');
    linhasColaboradores.push([id, String(pessoa.nome || '').toUpperCase(), pessoa.registro || '', pessoa.turno || '1º Turno', true, agora]);
    linhasEscala.push([mes, id, String(pessoa.nome || '').toUpperCase(), pessoa.registro || '', pessoa.turno || '1º Turno'].concat(dias).concat([true, agora]));
  });

  if (linhasColaboradores.length) planilha.getSheetByName(NOMES_ABAS.colaboradores).getRange(2, 1, linhasColaboradores.length, CABECALHOS.colaboradores.length).setValues(linhasColaboradores);
  if (linhasEscala.length) planilha.getSheetByName(NOMES_ABAS.escala).getRange(2, 1, linhasEscala.length, CABECALHOS.escala.length).setValues(linhasEscala);

  registrarHistorico_('CONFIGURAÇÃO INICIAL', `Dados iniciais criados para ${mes}.`, 'Sistema');
}

function obterBootstrap_(mesAno) {
  validarMesAno_(mesAno);
  const planilha = SpreadsheetApp.getActiveSpreadsheet();
  const colaboradores = lerColaboradoresAtivos_();
  const postos = lerPostosAtivos_();
  const abaEscala = planilha.getSheetByName(NOMES_ABAS.escala);
  const valores = obterValoresSemCabecalho_(abaEscala, CABECALHOS.escala.length);
  const mapaColaboradores = {};
  colaboradores.forEach(item => { mapaColaboradores[item.id] = item; });

  let escala = valores
    .filter(linha => String(linha[0]) === mesAno && valorBooleano_(linha[36]))
    .map(linha => ({
      id: String(linha[1] || ''),
      nome: String(linha[2] || mapaColaboradores[String(linha[1])]?.nome || '').toUpperCase(),
      registro: String(linha[3] || mapaColaboradores[String(linha[1])]?.registro || ''),
      turno: String(linha[4] || mapaColaboradores[String(linha[1])]?.turno || '1º Turno'),
      dias: linha.slice(5, 36).map(valor => String(valor || '')),
      ativo: true
    }))
    .filter(item => mapaColaboradores[item.id] && mapaColaboradores[item.id].ativo !== false);

  if (!escala.length) {
    escala = colaboradores.map(item => ({
      id: item.id,
      nome: item.nome,
      registro: item.registro,
      turno: item.turno,
      dias: Array(31).fill(''),
      ativo: true
    }));
  }

  escala.sort((a, b) => `${a.turno}${a.nome}`.localeCompare(`${b.turno}${b.nome}`));
  return {
    sucesso: true,
    versao: VERSAO_API,
    equipe: EQUIPE_PADRAO,
    mesAno,
    postos,
    colaboradores,
    escala,
    atualizadoEm: new Date().toISOString()
  };
}

function obterRelatorio_(parametros) {
  const inicio = String(parametros.dataInicio || '0000-00-00');
  const fim = String(parametros.dataFim || '9999-12-31');
  const turno = String(parametros.turno || 'todos');
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.fechamento);
  const valores = obterValoresSemCabecalho_(aba, CABECALHOS.fechamento.length);

  const registros = valores.map(linha => {
    const dataISO = normalizarDataISO_(linha[10] || linha[0]);
    return {
      data: textoData_(linha[0]),
      colaborador: String(linha[1] || ''),
      registro: String(linha[2] || ''),
      turno: String(linha[3] || ''),
      setorPosto: String(linha[4] || ''),
      quantidade: Number(linha[5] || 0),
      protocolo: String(linha[6] || ''),
      dataEnvio: textoData_(linha[7]),
      horaEnvio: textoHora_(linha[8]),
      colaboradorId: String(linha[9] || ''),
      dataISO
    };
  }).filter(item => item.dataISO >= inicio && item.dataISO <= fim && (turno === 'todos' || item.turno === turno));

  registros.sort((a, b) => `${b.dataISO}${b.horaEnvio}`.localeCompare(`${a.dataISO}${a.horaEnvio}`));
  return { sucesso: true, registros, quantidade: registros.length, atualizadoEm: new Date().toISOString() };
}

function salvarFechamento_(dados) {
  const obrigatorios = ['data', 'colaborador', 'registro', 'turno', 'setorPosto', 'quantidade', 'protocolo'];
  obrigatorios.forEach(campo => {
    if (dados[campo] === undefined || dados[campo] === null || String(dados[campo]).trim() === '') throw new Error(`Campo obrigatório não informado: ${campo}.`);
  });
  const quantidade = Number(dados.quantidade);
  if (!Number.isInteger(quantidade) || quantidade <= 0) throw new Error('A quantidade deve ser um número inteiro maior que zero.');

  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.fechamento);
  const protocolo = String(dados.protocolo).trim();
  if (protocoloExiste_(aba, protocolo)) {
    return { sucesso: true, duplicado: true, protocolo, mensagem: 'Protocolo já registrado. Nenhuma linha duplicada foi criada.' };
  }

  const criadoEm = new Date();
  const linha = [
    dados.data,
    String(dados.colaborador).trim().toUpperCase(),
    String(dados.registro).trim(),
    String(dados.turno).trim(),
    String(dados.setorPosto).trim(),
    quantidade,
    protocolo,
    dados.dataEnvio || Utilities.formatDate(criadoEm, fuso_(), 'dd/MM/yyyy'),
    dados.horaEnvio || Utilities.formatDate(criadoEm, fuso_(), 'HH:mm:ss'),
    dados.colaboradorId || '',
    dados.dataISO || normalizarDataISO_(dados.data),
    criadoEm
  ];
  aba.appendRow(linha);
  const ultimaLinha = aba.getLastRow();
  aba.getRange(ultimaLinha, 6).setNumberFormat('0');
  aba.getRange(ultimaLinha, 12).setNumberFormat('dd/MM/yyyy HH:mm:ss');
  if (ultimaLinha % 2 === 0) aba.getRange(ultimaLinha, 1, 1, CABECALHOS.fechamento.length).setBackground('#e6faff');

  atualizarRegistroColaborador_(dados.colaboradorId, dados.registro);
  registrarHistorico_('FECHAMENTO DE CARGAS', `${protocolo} • ${dados.colaborador} • ${quantidade} carga(s).`, dados.registro);
  return { sucesso: true, protocolo, mensagem: 'Registro salvo com sucesso.' };
}

function salvarColaborador_(dados) {
  const pessoa = dados.colaborador || {};
  if (!pessoa.id || !pessoa.nome || !pessoa.turno) throw new Error('Dados do colaborador incompletos.');
  const agora = new Date();
  const linha = [pessoa.id, String(pessoa.nome).toUpperCase(), pessoa.registro || '', pessoa.turno, pessoa.ativo !== false, agora];
  upsertPorChave_(NOMES_ABAS.colaboradores, CABECALHOS.colaboradores.length, 1, pessoa.id, linha);
  if (dados.mesAno) salvarLinhaEscala_(dados.mesAno, pessoa);
  registrarHistorico_('SALVAR COLABORADOR', `${pessoa.nome} • ${pessoa.turno}.`, 'Administrador');
  return { sucesso: true, mensagem: 'Colaborador salvo.' };
}

function excluirColaborador_(dados) {
  const id = String(dados.colaboradorId || '');
  if (!id) throw new Error('ID do colaborador não informado.');
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.colaboradores);
  const linha = localizarLinha_(aba, 1, id);
  if (!linha) throw new Error('Colaborador não encontrado.');
  aba.getRange(linha, 5).setValue(false);
  aba.getRange(linha, 6).setValue(new Date());
  registrarHistorico_('DESATIVAR COLABORADOR', id, 'Administrador');
  return { sucesso: true, mensagem: 'Colaborador desativado.' };
}

function salvarPosto_(dados) {
  const posto = dados.posto || {};
  if (!posto.codigo || !posto.local) throw new Error('Dados do posto incompletos.');
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.postos);
  if (dados.codigoOriginal && dados.codigoOriginal !== posto.codigo) {
    const antiga = localizarLinha_(aba, 1, dados.codigoOriginal);
    if (antiga) aba.getRange(antiga, 4).setValue(false);
  }
  const linha = [posto.codigo, posto.local, posto.setor || posto.local, posto.ativo !== false, new Date()];
  upsertPorChave_(NOMES_ABAS.postos, CABECALHOS.postos.length, 1, posto.codigo, linha);
  registrarHistorico_('SALVAR POSTO', `${posto.codigo} • ${posto.local}.`, 'Administrador');
  return { sucesso: true, mensagem: 'Posto salvo.' };
}

function excluirPosto_(dados) {
  const codigo = String(dados.codigo || '');
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.postos);
  const linha = localizarLinha_(aba, 1, codigo);
  if (!linha) throw new Error('Posto não encontrado.');
  aba.getRange(linha, 4).setValue(false);
  aba.getRange(linha, 5).setValue(new Date());
  registrarHistorico_('DESATIVAR POSTO', codigo, 'Administrador');
  return { sucesso: true, mensagem: 'Posto desativado.' };
}

function salvarEscala_(dados) {
  validarMesAno_(dados.mesAno);
  const pessoa = dados.colaborador || {};
  if (!pessoa.id || !pessoa.nome) throw new Error('Colaborador da escala não informado.');
  salvarLinhaEscala_(dados.mesAno, pessoa);
  registrarHistorico_('SALVAR ESCALA', `${dados.mesAno} • ${pessoa.nome}.`, 'Administrador');
  return { sucesso: true, mensagem: 'Escala salva.' };
}

function salvarLinhaEscala_(mesAno, pessoa) {
  const dias = Array.from({ length: 31 }, (_, i) => pessoa.dias && pessoa.dias[i] || '');
  const linha = [mesAno, pessoa.id, String(pessoa.nome || '').toUpperCase(), pessoa.registro || '', pessoa.turno || '1º Turno']
    .concat(dias)
    .concat([pessoa.ativo !== false, new Date()]);
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.escala);
  const linhaExistente = localizarLinhaComposta_(aba, 1, mesAno, 2, pessoa.id);
  if (linhaExistente) aba.getRange(linhaExistente, 1, 1, linha.length).setValues([linha]);
  else aba.appendRow(linha);
}

function substituirColaborador_(dados) {
  validarMesAno_(dados.mesAno);
  const diaInicio = Number(dados.diaInicio || 1);
  if (diaInicio < 1 || diaInicio > 31) throw new Error('Dia inicial inválido.');
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.escala);
  const linhaOrigem = localizarLinhaComposta_(aba, 1, dados.mesAno, 2, dados.origemId);
  const linhaDestino = localizarLinhaComposta_(aba, 1, dados.mesAno, 2, dados.destinoId);
  if (!linhaOrigem || !linhaDestino) throw new Error('As duas escalas precisam existir no mês selecionado.');

  const origem = aba.getRange(linhaOrigem, 1, 1, CABECALHOS.escala.length).getValues()[0];
  const destino = aba.getRange(linhaDestino, 1, 1, CABECALHOS.escala.length).getValues()[0];
  for (let dia = diaInicio; dia <= 31; dia++) {
    const indice = 4 + dia;
    destino[indice] = origem[indice] || '';
    origem[indice] = '';
  }
  origem[37] = new Date();
  destino[37] = new Date();
  aba.getRange(linhaOrigem, 1, 1, origem.length).setValues([origem]);
  aba.getRange(linhaDestino, 1, 1, destino.length).setValues([destino]);

  const nomeOrigem = origem[2];
  const nomeDestino = destino[2];
  SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.substituicoes).appendRow([
    Utilities.getUuid(), dados.mesAno, dados.origemId, nomeOrigem, dados.destinoId, nomeDestino, diaInicio, new Date()
  ]);
  registrarHistorico_('SUBSTITUIÇÃO', `${dados.mesAno} • ${nomeOrigem} → ${nomeDestino} • dia ${diaInicio}.`, 'Administrador');
  return { sucesso: true, mensagem: 'Substituição aplicada.' };
}

function copiarMes_(dados) {
  validarMesAno_(dados.mesOrigem);
  validarMesAno_(dados.mesDestino);
  if (dados.mesOrigem === dados.mesDestino) throw new Error('O mês de destino deve ser diferente.');
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.escala);
  const valores = obterValoresSemCabecalho_(aba, CABECALHOS.escala.length).filter(linha => String(linha[0]) === dados.mesOrigem && valorBooleano_(linha[36]));
  if (!valores.length) throw new Error('O mês de origem não possui escala salva.');
  valores.forEach(linha => {
    const nova = linha.slice();
    nova[0] = dados.mesDestino;
    nova[37] = new Date();
    const existente = localizarLinhaComposta_(aba, 1, dados.mesDestino, 2, nova[1]);
    if (existente) aba.getRange(existente, 1, 1, nova.length).setValues([nova]);
    else aba.appendRow(nova);
  });
  registrarHistorico_('COPIAR MÊS', `${dados.mesOrigem} → ${dados.mesDestino}.`, 'Administrador');
  return { sucesso: true, mensagem: 'Mês copiado.' };
}

function sincronizarTudo_(dados) {
  validarMesAno_(dados.mesAno);
  const postos = dados.postos || {};
  const escala = Array.isArray(dados.escala) ? dados.escala : [];
  Object.keys(postos).forEach(codigo => salvarPosto_({ posto: { codigo, ...postos[codigo] } }));
  escala.forEach(pessoa => {
    salvarColaborador_({ colaborador: pessoa });
    salvarLinhaEscala_(dados.mesAno, pessoa);
  });
  registrarHistorico_('SINCRONIZAÇÃO COMPLETA', `${dados.mesAno} • ${escala.length} colaborador(es).`, 'Administrador');
  return { sucesso: true, mensagem: 'Sincronização concluída.' };
}

function lerColaboradoresAtivos_() {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.colaboradores);
  return obterValoresSemCabecalho_(aba, CABECALHOS.colaboradores.length)
    .map(linha => ({ id: String(linha[0] || ''), nome: String(linha[1] || '').toUpperCase(), registro: String(linha[2] || ''), turno: String(linha[3] || ''), ativo: valorBooleano_(linha[4]) }))
    .filter(item => item.id && item.nome && item.ativo);
}

function lerPostosAtivos_() {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.postos);
  const postos = {};
  obterValoresSemCabecalho_(aba, CABECALHOS.postos.length).forEach(linha => {
    const codigo = String(linha[0] || '');
    if (codigo && valorBooleano_(linha[3])) postos[codigo] = { local: String(linha[1] || codigo), setor: String(linha[2] || linha[1] || codigo), ativo: true };
  });
  return postos;
}

function atualizarRegistroColaborador_(id, registro) {
  if (!id || !registro) return;
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.colaboradores);
  const linha = localizarLinha_(aba, 1, id);
  if (!linha) return;
  aba.getRange(linha, 3).setValue(String(registro));
  aba.getRange(linha, 6).setValue(new Date());
}

function protocoloExiste_(aba, protocolo) {
  if (aba.getLastRow() <= 1) return false;
  return Boolean(aba.getRange(2, 7, aba.getLastRow() - 1, 1).createTextFinder(protocolo).matchEntireCell(true).findNext());
}

function upsertPorChave_(nomeAba, quantidadeColunas, colunaChave, chave, linha) {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(nomeAba);
  const existente = localizarLinha_(aba, colunaChave, chave);
  if (existente) aba.getRange(existente, 1, 1, quantidadeColunas).setValues([linha]);
  else aba.appendRow(linha);
}

function localizarLinha_(aba, coluna, valor) {
  if (!valor || aba.getLastRow() <= 1) return 0;
  const encontrado = aba.getRange(2, coluna, aba.getLastRow() - 1, 1).createTextFinder(String(valor)).matchEntireCell(true).findNext();
  return encontrado ? encontrado.getRow() : 0;
}

function localizarLinhaComposta_(aba, colunaA, valorA, colunaB, valorB) {
  if (aba.getLastRow() <= 1) return 0;
  const valores = aba.getRange(2, 1, aba.getLastRow() - 1, Math.max(colunaA, colunaB)).getValues();
  for (let i = 0; i < valores.length; i++) {
    if (String(valores[i][colunaA - 1]) === String(valorA) && String(valores[i][colunaB - 1]) === String(valorB)) return i + 2;
  }
  return 0;
}

function obterValoresSemCabecalho_(aba, colunas) {
  const linhas = aba.getLastRow() - 1;
  return linhas > 0 ? aba.getRange(2, 1, linhas, colunas).getValues() : [];
}

function validarAdmin_(senha) {
  if (!senha) throw new Error('Senha administrativa não informada.');
  const esperado = PropertiesService.getScriptProperties().getProperty(PROPRIEDADE_HASH_ADMIN) || HASH_ADMIN_PADRAO;
  if (sha256_(String(senha)) !== esperado) throw new Error('Senha administrativa inválida.');
}

function validarMesAno_(valor) {
  if (!/^\d{4}-\d{2}$/.test(String(valor || ''))) throw new Error('Mês inválido. Use o formato AAAA-MM.');
}

function registrarHistorico_(acao, detalhes, usuario) {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(NOMES_ABAS.historico);
  if (aba) aba.appendRow([new Date(), acao, detalhes, usuario || 'Sistema']);
}

function lerCorpo_(e) {
  if (e && e.postData && e.postData.contents) {
    try { return JSON.parse(e.postData.contents); } catch (_) { /* tenta parâmetros */ }
  }
  return (e && e.parameter) || {};
}

function responder_(objeto, callback) {
  const json = JSON.stringify(objeto);
  const callbackSeguro = String(callback || '');
  if (callbackSeguro && /^[A-Za-z_$][0-9A-Za-z_$]*$/.test(callbackSeguro)) {
    return ContentService.createTextOutput(`${callbackSeguro}(${json});`).setMimeType(ContentService.MimeType.JAVASCRIPT);
  }
  return ContentService.createTextOutput(json).setMimeType(ContentService.MimeType.JSON);
}

function sha256_(texto) {
  return Utilities.computeDigest(Utilities.DigestAlgorithm.SHA_256, texto, Utilities.Charset.UTF_8)
    .map(byte => (byte < 0 ? byte + 256 : byte).toString(16).padStart(2, '0'))
    .join('');
}

function slug_(texto) {
  return String(texto || '').normalize('NFD').replace(/[\u0300-\u036f]/g, '').replace(/[^A-Za-z0-9]+/g, '-').replace(/^-+|-+$/g, '').toLowerCase();
}

function valorBooleano_(valor) {
  if (valor === false || String(valor).toLowerCase() === 'false' || String(valor) === '0') return false;
  return true;
}

function mesAtual_() {
  return Utilities.formatDate(new Date(), fuso_(), 'yyyy-MM');
}

function fuso_() {
  return Session.getScriptTimeZone() || 'America/Sao_Paulo';
}

function normalizarDataISO_(valor) {
  if (valor instanceof Date && !isNaN(valor)) return Utilities.formatDate(valor, fuso_(), 'yyyy-MM-dd');
  const texto = String(valor || '').trim();
  if (/^\d{4}-\d{2}-\d{2}$/.test(texto)) return texto;
  const partes = texto.split('/');
  if (partes.length === 3) return `${partes[2]}-${partes[1].padStart(2, '0')}-${partes[0].padStart(2, '0')}`;
  return '';
}

function textoData_(valor) {
  if (valor instanceof Date && !isNaN(valor)) return Utilities.formatDate(valor, fuso_(), 'dd/MM/yyyy');
  return String(valor || '');
}

function textoHora_(valor) {
  if (valor instanceof Date && !isNaN(valor)) return Utilities.formatDate(valor, fuso_(), 'HH:mm:ss');
  return String(valor || '');
}

function mensagemErro_(erro) {
  return erro && erro.message ? erro.message : String(erro || 'Erro desconhecido.');
}
