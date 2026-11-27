# Lab05 S01 — Proposta: Acessibilidade e Desempenho de Serviços Digitais do SUS

> Proposta da Sprint 1 (Lab05S01) · Elaborado por Henrique Lima Volponi · Fontes acessadas em 27/11/2026

Este estudo avalia a **acessibilidade** e o **desempenho web** do Meu SUS Digital — o aplicativo e portal oficial do Ministério da Saúde para o cidadão — medindo-o de fora, como faria um usuário comum, com ferramentas automatizadas (Lighthouse e axe-core) à luz da WCAG 2.2 e da ISO/IEC 25010. Esta proposta define o objeto e comprova seus três critérios, a pergunta de pesquisa, o caminho do estudo, a classificação nas 7 categorias, o GQM e as hipóteses e variáveis.

## 1. O software e os três critérios

O objeto de estudo é o **Meu SUS Digital** (antigo Conecte SUS Cidadão), o aplicativo e portal web oficial do Ministério da Saúde para o cidadão, desenvolvido e mantido pelo DATASUS. O estudo mede as superfícies web do serviço (portal/PWA) de fora, como um usuário comum.

| Critério | O que mostra | Evidência e fonte (acesso em 27/11/2026) |
| --- | --- | --- |
| **Real** | App/portal oficial do Ministério da Saúde, não um protótipo | Desenvolvedor "Serviços e Informações do Brasil", © DATASUS – Ministério da Saúde, categoria Medicina ([App Store](https://apps.apple.com/br/app/meu-sus-digital/id1045754608)) |
| **Em operação** | Versão mantida e atualizada com frequência | iOS 13.21.0 (atualizado em 11/nov) e builds Android recentes, ex. 73.26.00 ([App Store](https://apps.apple.com/br/app/meu-sus-digital/id1045754608), [APKMirror](https://www.apkmirror.com/apk/governo-do-brasil-2/meu-sus-digital/)) |
| **Alto impacto** | Dezenas de milhões de usuários; integra o maior portal de serviços do país | 29 mi de usuários mensais ativos e 60 mi de downloads em set/2025 ([Mobile Time](https://www.mobiletime.com.br/noticias/15/09/2025/sus-digital-saude-29-mi/)); 8 mi de usuários únicos/mês e 49 mi de downloads em mai/2024 ([Mobile Time](https://www.mobiletime.com.br/noticias/09/05/2024/meu-sus-digital-tem-8-milhoes-de-usuarios-mensais/)); acesso via gov.br, que atingiu 175 mi de usuários e ~1 bi de acessos em jan–fev/2026 ([Agência Gov](https://agenciagov.ebc.com.br/noticias/202603/gov-br-alcanca-a-marca-de-175-milhoes-de-usuarios-1-bilhao-acessos)) |

O app tem avaliação 3,7/5 com 31 mil classificações na App Store brasileira, reforçando o alcance do serviço. *Observação: as métricas de 2024 e 2025 não são diretamente comparáveis (definições de métrica distintas); cada número é citado conforme a fonte.*

## 2. Pergunta de pesquisa

**Pergunta principal.** Em que medida o Meu SUS Digital atende aos critérios de acessibilidade (WCAG 2.2) e de desempenho web percebido por um usuário comum, e como esses resultados variam entre páginas/fluxos e ao longo do dia?

**Subperguntas.**

1. Quais violações de acessibilidade WCAG 2.2 (níveis A/AA) são detectáveis automaticamente nas principais telas/fluxos públicos, e qual a frequência e a severidade delas?
2. Qual o desempenho web das principais páginas (score Lighthouse e Core Web Vitals: LCP, TBT/INP, CLS) e o peso de cada página?
3. Esses indicadores variam conforme a página/fluxo e o horário da medição (pico vs. fora de pico)?

## 3. Caminho(s) do estudo

O caminho principal é **avaliar a qualidade do produto** segundo a ISO/IEC 25010, com foco em **acessibilidade** (conformidade com a WCAG 2.2, via axe-core e Lighthouse), combinado com **medir o serviço de fora** (desempenho e peso das páginas, observados como um usuário comum). Combinar caminhos tende a gerar evidência mais forte, como valoriza o enunciado.

**Por quê.** Acessibilidade e desempenho são diretamente perceptíveis pelo cidadão, mensuráveis de fora com ferramentas padronizadas e abertas, e têm respaldo legal (Lei Brasileira de Inclusão – Lei 13.146/2015 – e o eMAG, modelo de acessibilidade em governo eletrônico), o que torna o resultado acionável.

**Ética.** Toda a medição é externa, sem teste de carga ou estresse; respeitamos os termos de uso e o robots.txt, limitamos a no máximo 1 requisição por segundo e não coletamos dados pessoais (medimos apenas páginas públicas, sem login).

## 4. As 7 categorias de pesquisa

| # | Categoria | Classificação | Justificativa |
| --- | --- | --- | --- |
| 1 | Natureza | Aplicada | Gera conhecimento para melhorar um serviço público real em operação. |
| 2 | Objetivos | Descritiva (com viés exploratório) | Descreve o nível de acessibilidade e desempenho; caracteriza violações ainda não mapeadas. |
| 3 | Abordagem | Quantitativa (apoio qualitativo) | Métricas numéricas de Lighthouse/axe; a categorização das violações WCAG tem componente qualitativo. |
| 4 | Procedimentos | Observacional / de medição (não experimental) | Mede o artefato em produção, de fora, sem manipular tratamentos; a comparação por horário adiciona leve componente quase-experimental. |
| 5 | Tempo | Transversal com repetições | Snapshot das páginas, repetido em horários/dias (aproxima-se de longitudinal curto para a RQ3). |
| 6 | Controle | Baixo | Ambiente real de produção, sem randomização nem isolamento de causas; controlamos apenas a instrumentação (mesmo aparelho, rede, ferramenta e versão). |
| 7 | Nível de evidência | Observacional | Menor que a de um experimento controlado; forte validade externa (software real em produção), menor validade interna. |

## 5. GQM (Goal–Question–Metric)

**Objetivo (template de Basili).** Analisar o *Meu SUS Digital (portal web)* com o propósito de *caracterizar e avaliar*, com respeito à *acessibilidade (WCAG 2.2) e ao desempenho web percebido*, do ponto de vista do *cidadão usuário*, no contexto da *medição externa automatizada das principais telas/fluxos públicos em produção*.

| Pergunta | Métrica | Escala |
| --- | --- | --- |
| Q1. Qual o nível de conformidade de acessibilidade? | Nº de violações WCAG por página (axe-core) | Razão (contagem) |
| Q1 | Violações por nível (A/AA) e por severidade | Ordinal / contagem |
| Q1 | Score de acessibilidade do Lighthouse (0–100) | Intervalar |
| Q2. Qual o desempenho web percebido? | Performance score do Lighthouse (0–100) | Intervalar |
| Q2 | LCP — Largest Contentful Paint (s) | Razão |
| Q2 | TBT (ms) / INP (ms) | Razão |
| Q2 | CLS — Cumulative Layout Shift (adimensional) | Razão |
| Q2 | Peso da página (KB) e nº de requisições | Razão |
| Q3. Como variam entre páginas e horários? | Dispersão entre páginas (desvio-padrão / IQR) | Razão |
| Q3 | Diferença de LCP/score entre pico e fora de pico | Razão (diferença) |

## 6. Hipóteses e variáveis

O estudo é majoritariamente descritivo; as hipóteses abaixo orientam a parte comparativa (RQ3) e os testes estatísticos, reaproveitando o Lab04 (escolha do teste, erro tipo I e poder).

- **H1 (horário).** H₀: não há diferença no LCP (nem no performance score) entre horários de pico e fora de pico. H₁: há diferença.
- **H2 (tipo de página).** H₀: o score de acessibilidade não difere entre tipos de página/fluxo. H₁: difere.

| Tipo | Variável | Operacionalização |
| --- | --- | --- |
| Independente (fator) | Horário da medição | Pico vs. fora de pico (faixas definidas) |
| Independente (fator) | Página/fluxo | Conjunto fixo das principais telas públicas |
| Independente (opcional) | Plataforma emulada | Mobile vs. desktop (Lighthouse) |
| Dependente | Acessibilidade | Nº de violações WCAG; score Lighthouse (0–100) |
| Dependente | Desempenho | Performance score; LCP; TBT/INP; CLS; peso (KB) |
| Controle | Instrumentação | Mesma máquina, rede, ferramenta e versão; mesmo throttling do Lighthouse |
| Controle | Repetições | 5 execuções por página/condição; usar a mediana |
| Controle | Versão medida | Mesma versão do portal registrada por rodada; ≤ 1 requisição/segundo |

*As ameaças à validade (4 tipos) ficam para a tarefa do Caio e se conectam diretamente ao baixo controle e à natureza observacional registrados acima.*

## Fontes

- gov.br atinge 175 milhões de usuários e ~1 bilhão de acessos (jan–fev/2026) — [Agência Gov, 24/03/2026](https://agenciagov.ebc.com.br/noticias/202603/gov-br-alcanca-a-marca-de-175-milhoes-de-usuarios-1-bilhao-acessos)
- Meu SUS Digital: 29 mi de MAUs e 60 mi de downloads — [Mobile Time, 15/09/2025](https://www.mobiletime.com.br/noticias/15/09/2025/sus-digital-saude-29-mi/)
- Meu SUS Digital: 8 mi de usuários únicos/mês e 49 mi de downloads — [Mobile Time, 09/05/2024](https://www.mobiletime.com.br/noticias/09/05/2024/meu-sus-digital-tem-8-milhoes-de-usuarios-mensais/)
- Meu SUS Digital na App Store (desenvolvedor, versão, avaliação) — [App Store (Brasil)](https://apps.apple.com/br/app/meu-sus-digital/id1045754608)
- Versões Android do app — [APKMirror](https://www.apkmirror.com/apk/governo-do-brasil-2/meu-sus-digital/)
