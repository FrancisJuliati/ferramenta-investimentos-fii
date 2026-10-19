# Ferramenta de Controle de Investimentos

Planilha em Excel que simula o acúmulo de patrimônio com aportes mensais e divide o valor investido entre tipos de Fundos Imobiliários (FIIs), de acordo com o perfil de investidor.

Projeto desenvolvido no curso **Santander - Excel com IA e Claude**, da DIO.me.

> **Aviso:** todos os valores da planilha (salário, aporte, taxas) são fictícios e servem apenas de exemplo. Este projeto não é recomendação de investimento.

## O que a ferramenta faz

- Calcula o patrimônio acumulado a partir do aporte mensal, do prazo em anos e da taxa de rendimento.
- Estima os dividendos mensais gerados por esse patrimônio.
- Compara cenários de 2, 5, 10, 20 e 30 anos, com os dividendos de cada um.
- Sugere um investimento mensal equivalente a 30% do salário, como referência. O aporte usado nos cálculos é definido pelo usuário.
- Divide o aporte entre seis tipos de FII (Papel, Tijolo, Híbridos, FOFs, Hotelaria e Desenvolvimento) conforme o perfil escolhido: Conservador, Moderado ou Agressivo.
- Exibe a distribuição em gráficos de pizza.

## Como usar

Na aba **FERRAMENTA**, preencha:

| Campo | O que informar |
|---|---|
| Salário | Renda mensal, usada para calcular o investimento sugerido |
| Rendimento carteira | Taxa mensal aplicada sobre o patrimônio para estimar os dividendos |
| Valor (investimento mensal) | Aporte mensal em R$ |
| Número de anos | Prazo da projeção |
| Taxa de rendimento | Taxa mensal usada para acumular o patrimônio |
| Perfil | Escolha na lista: Conservador, Moderado ou Agressivo |

Os resultados (patrimônio, dividendos, cenários, alocação e gráficos) são recalculados automaticamente.

## Estrutura

| Aba | Conteúdo |
|---|---|
| FERRAMENTA | Entradas, resultados, cenários, alocação por tipo de FII e gráficos |
| CHAVES | Tabela de apoio com os percentuais de cada perfil. Cada linha tem uma chave no formato `PERFIL-TIPO` (por exemplo, `MODERADO-TIJOLO`), consultada pela aba principal |

### Alocação por perfil

| Tipo de FII | Conservador | Moderado | Agressivo |
|---|---|---|---|
| Papel | 30% | 32% | 50% |
| Tijolo | 50% | 40% | 10% |
| Híbridos | 10% | 13% | 5% |
| FOFs | 10% | 5% | 5% |
| Hotelaria | 0% | 5% | 20% |
| Desenvolvimento | 0% | 5% | 10% |

## Como funciona

- **Patrimônio acumulado:** função `VF` (valor futuro), com aportes ao fim de cada mês, taxa mensal e reinvestimento integral.
- **Dividendos mensais:** patrimônio acumulado multiplicado pelo rendimento da carteira.
- **Alocação:** `PROCV` busca na aba CHAVES o percentual da chave `PERFIL-TIPO` e o multiplica pelo aporte.
- **Nomes definidos:** `SALARIO`, `RENDIMENTO_CARTEIRA`, `APORTE`, `QTD_ANOS` e `TAXA_MENSAL` deixam as fórmulas legíveis.

## Premissas e limitações

- As taxas são **mensais**. Os valores de exemplo (1,079% ao mês na acumulação e 1,08% ao mês na carteira) equivalem a cerca de 13,7% ao ano, um cenário otimista escolhido para ilustrar.
- Os valores são **nominais**: não descontam inflação, impostos nem custos de corretagem.
- Os percentuais por perfil são fixos e definidos pelo autor. Não vêm de análise de mercado.
- A planilha projeta, mas não acompanha a carteira real (tickers, cotas, preço médio).
- Cotas de FIIs oscilam e os dividendos variam. Projeções não garantem resultados futuros.

## Possíveis evoluções

- Cenários pessimista, base e otimista.
- Valores corrigidos pela inflação.
- Aporte com reajuste anual.
- Aba de controle da carteira real.

## Uso

Projeto de estudo, de uso livre para fins educacionais.

