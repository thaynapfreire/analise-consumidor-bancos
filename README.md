# Análise de Dados do consumidor de Bancos Brasileiros

Leitura comparada de três bases públicas sobre reclamação bancária no Brasil.

O objetivo não é ranquear instituições. É expor que as fontes disponíveis respondem a perguntas diferentes e chegam a conclusões incompatíveis sobre o mesmo banco, e tornar essa divergência visível e explicável.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | Dashboard interativo, oito seções, com mapa de regiões clicável |
| `documentacao.html` | Documentação técnica em página única, com a modelagem do cruzamento |

Ambos são HTML autocontido. Sem dependências, sem build, sem instalação. Abre no navegador.

## Achado principal

O Nubank aparece em 13º de 15 no ranking do Banco Central, 1º em volume no Consumidor.gov.br e com a melhor reputação entre os grandes no Reclame Aqui, no mesmo semestre.

As três leituras são defensáveis dentro das respectivas metodologias. Isso indica que a metodologia, e não o desempenho da instituição, está produzindo o resultado.

## Fontes

| Fonte | Natureza | Período |
|---|---|---|
| Banco Central, Ranking de Reclamações | Oficial, regulatória | 1º e 2º trimestres de 2026 |
| Banco Central, Registro de Demandas do Cidadão | Oficial, regulatória | 2024 |
| Banco Central, Relatório de Cidadania Financeira | Oficial, estatística | dezembro de 2024 |
| Consumidor.gov.br, Senacon/MJSP | Oficial, consensual | 2018 a julho de 2026 |
| Reclame Aqui | Privada, comercial | março a agosto de 2026 |

Os números do Reclame Aqui vieram exclusivamente de conteúdo público já indexado, sem coleta automatizada das páginas da plataforma, em respeito aos termos de uso. Isso limita a cobertura a quatro instituições, contra quinze no ranking do Banco Central.

## Limitações

Elas não são rodapé, são parte do resultado.

- **Viés de acesso.** As bases só registram quem sabe que pode reclamar e consegue chegar ao canal.
- **Viés de canal.** Público mais velho reclama por telefone, público mais jovem por plataforma digital. Isso distorce o ranking de temas em direções opostas.
- **Viés de tema.** O Banco Central só contabiliza descumprimento de norma sob sua supervisão.
- **Conflito de modelo de negócio.** O Reclame Aqui vende serviços de reputação às empresas que avalia.
- **Demografia inexistente.** Nenhuma das três fontes publica idade, gênero ou região de quem reclama. Os perfis no dashboard vêm de dados de uso de crédito, o que é uma inferência de um passo.
- **Defasagem.** Cerca de dezoito meses entre a camada demográfica e o ranking mais recente.

## Regras de linguagem

- A expressão "melhor banco" não é usada em nenhum ponto.
- Onde não há base, está escrito "sem dado" ou "não publicado". Nenhuma célula foi preenchida por estimativa.
- Inferências estão marcadas como inferência, separadas do que as fontes afirmam.

## Atualização

| Gatilho | Frequência |
|---|---|
| Ranking do Banco Central | Trimestral, cerca de 3 semanas após o fechamento |
| Consumidor.gov.br | Mensal |
| Reclame Aqui | Semestral |
| Relatório de Cidadania Financeira | Anual |

Quando uma fonte publicar dado que contradiga o dashboard, a versão anterior não é apagada. O bloco de verificação registra o que mudou e o que foi descartado, para que a leitura antiga continue auditável.

## Aviso

Este material é para análise. Não é recomendação de banco, de produto financeiro ou de investimento.
