---
name: analise-investimentos
description: Avalia ações brasileiras e fundos imobiliários (FIIs), diagnostica a carteira do usuário (exportada da Investidor10 ou colada) e procura oportunidades de diversificação, inclusive em quedas causadas por eventos como eleições. Use quando o usuário pedir para "analisar ação", "avaliar FII", "olhar minha carteira", "achar oportunidades", "preço-teto", "vale a pena comprar X", "comparar FIIs", "diversificar a carteira", ou citar tickers da B3 (ex.: PETR4, ITUB4, HGLG11, MXRF11).
---

# Análise de ações e FIIs

Análise fundamentalista **educativa** de ativos da B3 e da carteira do usuário. Responda sempre em português brasileiro.

## Regras que valem sempre

1. **Não é recomendação de investimento.** Claude não é analista credenciado pela CVM. Apresente análises, cenários e critérios; não diga "compre" ou "venda". Termine todo relatório com o aviso do fim deste arquivo.
2. **Dados com data e fonte.** Todo número (cotação, P/L, DY, vacância...) leva a fonte e a data de referência. Nunca invente nem "estime de memória" um indicador: se não conseguir buscar, escreva "não obtido" e diga ao usuário onde conferir.
3. **Queda não é oportunidade por si só.** Separe sempre *queda por ruído* (eleição, fluxo, juros) de *queda por deterioração* (lucro caindo, dívida subindo, perda de inquilino, inadimplência).
4. **Backup.** Se gerar planilha ou relatório, salve dentro do repositório (pasta `analises/`) e avise o usuário que o ambiente é temporário: o arquivo só fica guardado depois de commit e push, ou se ele baixar.

## Passo 1: obter a carteira

Não há conector da Investidor10. Peça ao usuário **uma** destas opções, nesta ordem de preferência:

- a planilha exportada da carteira na Investidor10 (se a opção de exportar estiver disponível na conta dele);
- uma cópia (texto ou print) da tela de ativos da carteira: ticker, quantidade, preço médio;
- uma lista digitada: `TICKER;QUANTIDADE;PRECO_MEDIO`.

Leia o arquivo e monte uma tabela: ticker, classe (ação, FII, ETF, BDR, renda fixa), setor/segmento, quantidade, preço médio, valor atual, % da carteira.

## Passo 2: buscar os dados

Use WebSearch/WebFetch. Fontes, nesta ordem:

- **Indicadores:** investidor10.com.br, statusinvest.com.br, fundamentus.com.br.
- **Documentos oficiais:** site de RI da empresa (release trimestral), CVM; para FIIs, relatório gerencial e informe mensal (FundosNet/B3, site da gestora).
- **Contexto:** notícias dos últimos 30 dias sobre o ativo e o setor.

Se o acesso a um site falhar por bloqueio de rede, diga qual site foi bloqueado e sugira liberar o domínio nas configurações de rede do ambiente; siga com as fontes que funcionarem.

## Passo 3: diagnosticar a carteira

Calcule e mostre:

- alocação por classe (ações × FIIs × renda fixa × exterior) e por setor/segmento;
- concentração: maior ativo, top 5, número de ativos;
- **exposição a risco político**: % em estatais e setores regulados (petróleo, bancos públicos, energia, saneamento, Correios/infra) e % em empresas dolarizadas/exportadoras (proteção);
- FIIs: divisão tijolo × papel × híbrido/FoF e, nos de papel, indexador (IPCA × CDI);
- lacunas de diversificação: setores ausentes, excesso num só segmento, ausência de proteção cambial ou de renda fixa.

## Passo 4: triagem de oportunidades

Quando o usuário quiser aproveitar quedas (ex.: período eleitoral):

1. Liste ativos (da carteira e do mercado) com queda relevante no período, e compare com o Ibovespa/IFIX no mesmo período.
2. Para cada um, responda: **o que mudou nos fundamentos?** Compare os últimos resultados com os anteriores. Se o lucro, a geração de caixa e o endividamento seguem iguais, a queda tende a ser de preço, não de valor.
3. Classifique a sensibilidade eleitoral:
   - **alta**: estatais e empresas com preço controlado (risco de intervenção, troca de diretoria, mudança de política de dividendos);
   - **média**: bancos, varejo e construção (sensíveis a juros e fiscal);
   - **baixa / proteção**: exportadoras dolarizadas, empresas com receita indexada.
4. Aplique a análise completa (passo 5) só nos candidatos que passarem no item 2.
5. Priorize os que **também melhoram a diversificação** encontrada no passo 3.

Pesquise o cenário político atual (resultado da eleição, falas sobre política econômica, curva de juros) antes de concluir. Não presuma o resultado.

## Passo 5: análise individual

- Ações: siga `references/acoes.md`.
- FIIs: siga `references/fiis.md`.

Os dois arquivos terminam numa nota de 0 a 10 com critérios fixos, para permitir comparar ativos entre si.

## Passo 6: entregar

Formato do relatório:

1. **Resumo** (3 a 5 linhas): situação da carteira e principais achados.
2. **Diagnóstico da carteira** (tabela de alocação e lacunas).
3. **Ativos analisados**: tabela comparativa (ticker, preço, preço-teto, margem de segurança, nota, sensibilidade eleitoral, principal risco).
4. **Detalhe por ativo**: pontos fortes, riscos, o que acompanhar (próximo resultado, vencimento de contrato, assembleia).
5. **Ideias de diversificação**: classes/setores que faltam, com exemplos de ativos para o usuário estudar, sem ordem de compra.
6. **Fontes e datas.**
7. **Aviso:**

> Esta análise é educativa e não constitui recomendação de investimento. Os dados podem estar desatualizados; confirme nas fontes oficiais antes de decidir. Rentabilidade passada não garante rentabilidade futura. Para recomendação personalizada, procure um profissional certificado (CNPI, CFP ou consultor CVM).

Se o usuário pedir, gere também uma planilha (`anthropic-skills:xlsx`) com a tabela comparativa.
