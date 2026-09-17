[README.md](https://github.com/user-attachments/files/32343781/README.md)
# Análise de Dados do consumidor de Bancos Brasileiros

Leitura comparada de três bases públicas sobre reclamação bancária no Brasil, com uma camada preditiva construída só com dados agregados.

**Acesse o Dashboard aqui: https://thaynapfreire.github.io/analise-consumidor-bancos/**

O objetivo não é ranquear instituições. É expor que as fontes disponíveis respondem a perguntas diferentes e chegam a conclusões incompatíveis sobre o mesmo banco, e tornar essa divergência visível e explicável.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | Dashboard interativo, versão 2: leitura das fontes, cruzamento, perfil de crédito com mapa de regiões clicável, personas e modelos preditivos |
| `documentacao.html` | Documentação técnica em página única, com a modelagem do cruzamento, a especificação dos modelos e os testes de validação |

Ambos são HTML autocontido. Sem dependências, sem build, sem instalação. Abre no navegador.

## Achado principal

O Nubank aparece em 13º de 15 no ranking do Banco Central, 1º em volume no Consumidor.gov.br e com a melhor reputação entre os grandes no Reclame Aqui, no mesmo semestre.

As três leituras são defensáveis dentro das respectivas metodologias. Isso indica que a metodologia, e não o desempenho da instituição, está produzindo o resultado.

## Novo na versão 2: camada preditiva

Os dados públicos são agregados, então nenhum modelo foi treinado em registros individuais. Cada modelo declara o que assume, quanto erra e o que não consegue prever.

| Modelo | O que faz | Como foi construído |
|---|---|---|
| Simulador de risco de inadimplência | Estima a probabilidade de inadimplência por faixa etária, região e CadÚnico, nas 30 combinações | Regressão logística calibrada nas marginais do Banco Central por ajuste proporcional iterativo, com duas especificações alternativas (aditiva e multiplicativa) para mostrar a incerteza |
| Projeção de clientes por modalidade | Quantas pessoas devem usar cada produto de crédito até 2027 | Envelope de três cenários (tendência, desaceleração e estagnação) a partir de dez/2020 e dez/2024 |
| Validação | O que foi testado, o que passou e o que foi descartado | Consistência das marginais, calibração do simulador e teste de persistência do ranking |

Destaques:

- O simulador reproduz todas as taxas publicadas dentro do arredondamento de 0,5 p.p. do Banco Central. As estimativas vão de 6,8% a 25,2% entre os perfis.
- No cenário de desaceleração, o crédito pessoal chega a 54,8 milhões de clientes em 2027 e fica a 3,5 milhões da dívida no cartão.
- A previsão do ranking do 3º trimestre de 2026 foi **descartada**: a persistência do ranking deu Spearman de 0,80 com apenas 5 instituições (p igual a 0,067), sem significância a 5%.
- A coluna de 2025 das projeções está pré registrada. Quando o Banco Central publicar a base de dez/2025, o erro de cada cenário será medido.

## Fontes

| Fonte | Natureza | Período |
|---|---|---|
| Banco Central, Ranking de Reclamações | Oficial, regulatória | 1º e 2º trimestres de 2026 |
| Banco Central, Registro de Demandas do Cidadão | Oficial, regulatória | 2024 |
| Banco Central, Relatório de Cidadania Financeira | Oficial, estatística | dezembro de 2020 e dezembro de 2024 |
| Consumidor.gov.br, Senacon/MJSP | Oficial, consensual | 2018 a julho de 2026 |
| Reclame Aqui | Privada, comercial | março a agosto de 2026 |
| IBGE, Censo Demográfico 2022 | Oficial, estatística | 2022, só como proxy de peso regional no simulador |

Os números do Reclame Aqui vieram exclusivamente de conteúdo público já indexado, sem coleta automatizada das páginas da plataforma, em respeito aos termos de uso. Isso limita a cobertura a quatro instituições, contra quinze no ranking do Banco Central.

## Limitações

Elas não são rodapé, são parte do resultado.

- **Viés de acesso.** As bases só registram quem sabe que pode reclamar e consegue chegar ao canal.
- **Viés de canal.** Público mais velho reclama por telefone, público mais jovem por plataforma digital. Isso distorce o ranking de temas em direções opostas.
- **Viés de tema.** O Banco Central só contabiliza descumprimento de norma sob sua supervisão.
- **Conflito de modelo de negócio.** O Reclame Aqui vende serviços de reputação às empresas que avalia.
- **Demografia inexistente.** Nenhuma das três fontes publica idade, gênero ou região de quem reclama. Os perfis no dashboard vêm de dados de uso de crédito, o que é uma inferência de um passo.
- **Defasagem.** Cerca de dezoito meses entre a camada demográfica e o ranking mais recente.
- **Modelos sem microdados.** O simulador assume ausência de interação entre idade, região e CadÚnico. Os pesos regionais usam o Censo 2022 como proxy e o peso do CadÚnico é derivado.
- **Projeções com dois pontos.** São cenários, não previsões com intervalo de confiança.

## Regras de linguagem

- A expressão "melhor banco" não é usada em nenhum ponto.
- Onde não há base, está escrito "sem dado" ou "não publicado". Nenhuma célula foi preenchida por estimativa.
- Inferências estão marcadas como inferência, separadas do que as fontes afirmam.
- Saída de modelo sempre aparece com a incerteza que a acompanha.

## Atualização

| Gatilho | Frequência |
|---|---|
| Ranking do Banco Central | Trimestral, cerca de 3 semanas após o fechamento. Com a tabela completa de índices, refazer o teste de persistência com n igual a 15 |
| Consumidor.gov.br | Mensal |
| Reclame Aqui | Semestral |
| Relatório de Cidadania Financeira | Anual. Recalibrar o simulador e medir o erro das projeções pré registradas |

Quando uma fonte publicar dado que contradiga o dashboard, a versão anterior não é apagada. O bloco de verificação registra o que mudou e o que foi descartado, para que a leitura antiga continue auditável.

## Aviso

Este material é para análise. Não é recomendação de banco, de produto financeiro ou de investimento.
