# Simulador de Investimentos em Fundos Imobiliários

## Objetivo
Construir uma ferramenta em Excel para simular aportes mensais, estimar patrimônio futuro e calcular uma renda mensal hipotética de dividendos, além de distribuir o aporte por seis categorias de fundos imobiliários conforme o perfil selecionado.

## Como usar
1. Abra `simulador_fundos_imobiliarios.xlsx` no Excel.
2. Na aba **Simulador**, altere as células amarelas: aporte mensal, prazo em anos, rendimento mensal, salário e perfil.
3. Confira o patrimônio estimado, os dividendos mensais, a sugestão de aporte de 30% do salário e as projeções de 2, 5, 10, 20 e 30 anos.
4. Troque o perfil na lista suspensa para atualizar a alocação e o gráfico.
5. Consulte **Configuracoes** para ver as premissas e os intervalos nomeados; consulte **Apoio** para conferir os percentuais.

## Perguntas de negócio respondidas
- **Quanto investir por mês?** O usuário informa o aporte na célula B6; a sugestão de referência aparece em B15 (30% do salário).
- **Por quantos anos?** Campo de prazo em B7.
- **Qual a taxa de rendimento mensal?** Campo B8.
- **Quanto de patrimônio vai acumular?** Resultado principal em B13 e projeções na tabela A19:D24.
- **Quanto receberá de dividendos por mês?** Estimativa em B14 e na coluna C da tabela de cenários.

## Fórmulas e lógica
- **VF / FV:** calcula o valor futuro dos aportes mensais com taxa mensal, número de períodos igual a anos × 12 e aporte como pagamento negativo para apresentar o patrimônio positivo. A fórmula considera aportes no fim de cada mês.
- **Dividendos estimados:** patrimônio acumulado × taxa mensal hipotética.
- **PROCV / VLOOKUP:** busca a percentagem de cada tipo de fundo para o perfil escolhido. A chave composta junta o perfil e o tipo de FII, por exemplo `Moderado|Shoppings`, permitindo que a busca identifique a combinação correta.
- **Validação de dados:** restringe a seleção do perfil às opções cadastradas na aba Apoio.

## Intervalos nomeados
- `aporte`: Simulador!$B$6
- `prazo_anos`: Simulador!$B$7
- `taxa_mensal`: Simulador!$B$8
- `salario`: Simulador!$B$9
- `Perfis`: Apoio!$G$3:$G$5

## Percentuais de alocação
Os percentuais são **premissas didáticas ilustrativas**, criadas para demonstrar a lógica da ferramenta; não foram extraídos de uma fonte de mercado nem constituem recomendação de investimento.

| Perfil | Recebíveis | Logísticos | Shoppings | Lajes | Renda urbana | Fundos de fundos |
|---|---:|---:|---:|---:|---:|---:|
| Conservador | 30% | 25% | 10% | 10% | 15% | 10% |
| Moderado | 25% | 20% | 15% | 10% | 15% | 15% |
| Arrojado | 15% | 20% | 20% | 15% | 15% | 15% |

Cada perfil soma 100%.

## O que foi acrescentado
- Painel visual com cores para diferenciar campos editáveis e resultados calculados.
- Intervalos nomeados para tornar as fórmulas mais legíveis.
- Tabela de projeção para 2, 5, 10, 20 e 30 anos.
- Lista suspensa de perfil, chave composta para a busca e gráfico de pizza da distribuição do aporte.
- Aba de configurações com premissas documentadas.

## Limitações importantes
Esta é uma simulação educativa, não uma previsão garantida de retorno nem recomendação financeira. A taxa mensal é mantida constante por simplicidade; a planilha não modela oscilações de preço, impostos, taxas, inflação, reinvestimento variável nem mudanças na distribuição de rendimentos dos FIIs. Os valores pré-preenchidos são exemplos, não dados pessoais.

## Publicação no GitHub
1. Crie um repositório público chamado `simulador-fundos-imobiliarios`.
2. Envie este README e a planilha `.xlsx`.
3. Tire capturas de tela do painel com pelo menos dois perfis diferentes.
4. No README do GitHub, inclua as capturas e explique brevemente o que mudou quando o perfil foi alterado.
