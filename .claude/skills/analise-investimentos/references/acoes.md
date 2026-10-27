# Análise de ações

## 1. Identificação

Ticker, empresa, setor, segmento de listagem (Novo Mercado, N2, N1, tradicional), controlador (privado, estatal, pulverizado), tipo da ação (ON/PN/Unit) e liquidez média diária.

## 2. Indicadores (buscar, nunca estimar)

| Grupo | Indicadores |
|---|---|
| Valuation | P/L, P/VP, EV/EBITDA, DY (12 meses), P/L médio de 5 anos |
| Rentabilidade | ROE, ROIC, margem bruta, margem EBITDA, margem líquida |
| Endividamento | Dívida líquida/EBITDA, dívida líquida/PL, liquidez corrente |
| Crescimento | CAGR de receita e de lucro em 5 anos |
| Dividendos | Payout, histórico de 5 anos, regularidade |

**Ajuste por setor:**
- **Bancos e seguradoras:** não use EV/EBITDA nem dívida/EBITDA. Use P/VP, ROE, índice de Basileia, inadimplência acima de 90 dias, custo do crédito.
- **Commodities (petróleo, mineração, papel e celulose, siderurgia):** use médias de ciclo, não o lucro de um ano bom. Considere preço da commodity e câmbio.
- **Elétricas e saneamento:** olhe prazo das concessões, revisão tarifária, risco regulatório.
- **Construção e varejo:** muito sensíveis à Selic; olhe a tendência da curva de juros.

## 3. Preço-teto (mostrar os dois e a média)

- **Bazin:** `média dos dividendos por ação dos últimos 5 anos ÷ 0,06`. Só faz sentido para pagadoras regulares.
- **Graham:** `√(22,5 × LPA × VPA)`. Não serve com LPA ou VPA negativo nem para bancos com P/VP estrutural alto.

`margem de segurança = (preço-teto − cotação) ÷ preço-teto`. Mostre em %.

## 4. Sinais de alerta (cada um vira um risco no relatório)

- Dívida líquida/EBITDA acima de 3x (fora de bancos e utilities).
- ROE em queda por 3 anos seguidos.
- Lucro sustentado por eventos não recorrentes (venda de ativo, crédito tributário).
- DY alto com lucro em queda (**armadilha de dividendos**) ou payout acima de 100%.
- Queima de caixa, aumentos de capital frequentes, recuperação judicial no setor.
- Governança: troca frequente de diretoria, conflitos com o controlador, ressalvas do auditor.
- **Estatais:** histórico de intervenção em preços, mudança de estatuto ou de política de dividendos.

## 5. Nota de 0 a 10

| Critério | Pontos |
|---|---|
| Valuation (P/L e P/VP abaixo da média histórica e do setor) | 0 a 2 |
| Rentabilidade (ROE/ROIC consistentes acima de 12%) | 0 a 2 |
| Endividamento saudável para o setor | 0 a 2 |
| Dividendos regulares e sustentáveis | 0 a 1,5 |
| Crescimento de receita e lucro | 0 a 1,5 |
| Governança | 0 a 1 |

Desconte até 2 pontos se a sensibilidade eleitoral/regulatória for alta e não houver margem de segurança que compense. Explique cada ponto dado.
