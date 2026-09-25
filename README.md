# Análise de Viagens a Serviço do Governo Federal (2023)

## Objetivo
Meu objetivo é saber o valor gasto em viagens por cargo.

## Fonte dos dados
Portal da Transparência do Governo Federal, seção Viagens, ano de 2023.
Os quatro arquivos usados são: Viagem.
Os dados não ficam no repositório por causa do tamanho (cerca de 1,1 GB).
Para reproduzir a análise, baixe os arquivos no Portal e salve-os em `data/raw`.

## Perguntas da análise
Serão definidas na próxima etapa.

## Estrutura do projeto
- `data/raw`: dados originais, sem alterações
- `data/processed`: dados tratados
- `notebooks`: análises em Jupyter
- `src`: scripts em Python
- `reports`: gráficos e resumo dos resultados

## Ferramentas
Python, pandas, matplotlib, Git, GitHub e VS Code.

### Status
Finalizado.

## Resultados da Análise

Análise das viagens a serviço do governo federal em 2023, com base na tabela `Viagem` do Portal da Transparência. O notebook completo com o código está em [`notebooks/03_analise.ipynb`](notebooks/03_analise.ipynb).

### 1. Quais órgãos superiores mais gastam com viagens?
| Órgão | Gasto total |
|---|---|
| Sem informação | R$ 684,8 milhões |
| Ministério da Justiça e Segurança Pública | R$ 319,7 milhões |
| Ministério da Defesa | R$ 302,9 milhões |
| Ministério da Educação | R$ 270,7 milhões |
| Ministério do Meio Ambiente e Mudança do Clima | R$ 113,4 milhões |

> **Observação:** a categoria "Sem informação" lidera com quase o dobro do 2º colocado, indicando falha de preenchimento na origem do dado. Mantida no ranking para documentar o problema.

### 2 e 3. Destinos mais frequentes (com e sem sigilo)
| Destino | Nº de viagens |
|---|---|
| Informações protegidas por sigilo* | 118.222 |
| Brasília/DF | 64.288 |
| Rio de Janeiro/RJ | 26.228 |
| São Paulo/SP | 24.621 |
| São José dos Campos/SP | 12.285 |

*\*Excluindo o sigilo, o ranking dos demais destinos não se altera — Brasília permanece em 1º.*

### 4 e 5. Destinos mais caros (com e sem sigilo)
| Destino | Gasto total |
|---|---|
| Informações protegidas por sigilo* | R$ 367,0 milhões |
| Brasília/DF | R$ 260,0 milhões |
| Rio de Janeiro/RJ | R$ 73,8 milhões |
| São Paulo/SP | R$ 60,5 milhões |
| Manaus/AM | R$ 26,1 milhões |

*\*Excluindo o sigilo, Boa Vista/RR entra no lugar dele na 10ª posição do ranking; os demais se mantêm.*

### 6. Os 5 cargos que mais viajam
| Cargo | Nº de viagens |
|---|---|
| Informações protegidas por sigilo | 118.222 |
| Professor do Magistério Superior | 54.570 |
| Professor Ens Básico Tecn Tecnológico | 37.476 |
| Contratado Lei 8745/93 - NI | 17.787 |
| Auditor Fiscal Federal Agropecuário | 16.582 |

### 7. Qual a duração média das viagens?
**5,89 dias** (mediana: 3 dias — a média é puxada por poucos casos extremos, com máximo de 501 dias).

### 8. Os 10 cargos com mais despesas
| Cargo | Gasto total |
|---|---|
| Informações protegidas por sigilo | R$ 367,0 milhões |
| Professor do Magistério Superior | R$ 109,9 milhões |
| Professor Ens Básico Tecn Tecnológico | R$ 52,0 milhões |
| Técnico do Seguro Social | R$ 45,4 milhões |
| Analista Ambiental | R$ 34,9 milhões |

### Decisões de qualidade de dados
- Viagens com `Despesas` negativa (8 casos) mantidas — refletem devolução líquida maior que o valor recebido, não erro de dado.
- Viagens "Não realizada" com `Despesas` zero são esperadas; "Realizada" com `Despesas` zero foi registrada como observação, sem correção aplicada.
- Categorias "Sem informação" (órgão) e "Informações protegidas por sigilo" (cargo/destino) foram mantidas nos rankings para expor a extensão do problema de dados incompletos/sigilosos na base.