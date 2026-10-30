[README.md](https://github.com/user-attachments/files/34180323/README.md)
# Análise de Dados do consumidor de Bancos Brasileiros

Leitura comparada de três bases públicas sobre reclamação bancária no Brasil, com uma camada preditiva construída só com dados agregados.

**Acesse o Dashboard aqui: https://thaynapfreire.github.io/analise-consumidor-bancos/**

O objetivo não é ranquear instituições. É expor que as fontes disponíveis respondem a perguntas diferentes e chegam a conclusões incompatíveis sobre o mesmo banco, e tornar essa divergência visível e explicável.

Dados atualizados em 29 de outubro de 2026.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | Dashboard interativo, versão 3: cinco abas com leitura das fontes, cruzamento por instituição, perfil de crédito e personas, modelos preditivos e metodologia |
| `documentacao.html` | Documentação técnica em página única, com a modelagem do cruzamento, a especificação dos modelos e os testes de validação |

Ambos são HTML autocontido. Sem dependências, sem build, sem instalação. Abre no navegador.

## Como o dashboard está organizado

| Aba | O que responde |
|---|---|
| Visão geral | Os três achados principais e um quadro de como ler cada fonte: o que conta, qual o denominador, qual a barreira de acesso e o que não publica |
| Instituições | Onde as fontes concordam e onde divergem, o caso Nubank e o detalhe de cada fonte, com o ranking do Banco Central por trimestre |
| Crédito e personas | Temas mais reclamados, perfil de quem usa crédito com mapa de regiões clicável, e as três personas que emergem do cruzamento |
| Modelos | Simulador de risco de inadimplência, mapa das 30 combinações e projeção de clientes por modalidade até 2027 |
| Metodologia | Validação dos modelos, limitações e fontes |

## Achado principal

O Nubank aparece em 13º de 15 no ranking do Banco Central do 3º trimestre de 2026, foi 1º em volume no Consumidor.gov.br em junho e julho e tem a melhor reputação entre os grandes no Reclame Aqui.

As três leituras são defensáveis dentro das respectivas metodologias. Isso indica que a metodologia, e não o desempenho da instituição, está produzindo o resultado.

O Itaú mostra o mesmo padrão no sentido oposto: subiu do 7º para o 3º lugar no ranking do Banco Central entre o 1º e o 3º trimestre, enquanto mantém nota 8,1 e reputação Ótima no Reclame Aqui.

## Camada preditiva

Os dados públicos são agregados, então nenhum modelo foi treinado em registros individuais. Cada modelo declara o que assume, quanto erra e o que não consegue prever.

| Modelo | O que faz | Como foi construído |
|---|---|---|
| Simulador de risco de inadimplência | Estima a probabilidade de inadimplência por faixa etária, região e CadÚnico, nas 30 combinações | Regressão logística calibrada nas marginais do Banco Central por ajuste proporcional iterativo, com duas especificações alternativas (aditiva e multiplicativa) para mostrar a incerteza |
| Projeção de clientes por modalidade | Quantas pessoas devem usar cada produto de crédito até 2027 | Envelope de três cenários (tendência, desaceleração e estagnação) a partir de dez/2020 e dez/2024 |
| Validação | O que foi testado, o que passou e o que foi descartado | Consistência das marginais, calibração do simulador e teste de persistência do ranking |

Destaques:

- O simulador reproduz todas as taxas publicadas dentro do arredondamento de 0,5 p.p. do Banco Central. As estimativas vão de 6,8% a 25,2% entre os perfis.
- No cenário de desaceleração, o crédito pessoal chega a 54,8 milhões de clientes em 2027 e fica a 3,5 milhões da dívida no cartão.
- A persistência do ranking do Banco Central foi **confirmada**. Com a tabela completa do 3º trimestre, o teste foi refeito com as 15 instituições: Spearman de 0,83 entre o 1º e o 3º trimestre, p menor que 0,001. Em julho, com apenas 5 instituições, o mesmo teste tinha dado 0,80 com p igual a 0,067, sem significância. A previsão do 4º trimestre continua fora do dashboard, porque cinco instituições andaram três posições ou mais em seis meses.
- A coluna de 2025 das projeções está pré registrada. Quando o Banco Central publicar a base de dez/2025, o erro de cada cenário será medido.
- Primeiro sinal da hipótese das projeções: no 3º trimestre de 2026, "operações de crédito, exceto consignado" foi o 2º tema mais reclamado no ranking do Banco Central, com 3.193 registros.

## Fontes

| Fonte | Natureza | Período |
|---|---|---|
| Banco Central, Ranking de Reclamações | Oficial, regulatória | 1º ao 3º trimestre de 2026 |
| Banco Central, Registro de Demandas do Cidadão | Oficial, regulatória | 2024 |
| Banco Central, Relatório de Cidadania Financeira | Oficial, estatística | dezembro de 2020 e dezembro de 2024 |
| Consumidor.gov.br, Senacon/MJSP | Oficial, consensual | 2018 a agosto de 2026. Indicadores por banco de junho de 2026 |
| Reclame Aqui | Privada, comercial | março a setembro de 2026, conforme a janela de cada página |
| IBGE, Censo Demográfico 2022 | Oficial, estatística | 2022, só como proxy de peso regional no simulador |

A tabela completa do ranking do 3º trimestre, com reclamações procedentes e número de clientes, veio da divulgação do Banco Central de 22/10/2026, conforme publicada por Finsiders Brasil e InfoMoney.

Os números do Reclame Aqui vieram exclusivamente de conteúdo público já indexado, sem coleta automatizada das páginas da plataforma, em respeito aos termos de uso. Isso limita a cobertura a quatro instituições, contra quinze no ranking do Banco Central.

## Limitações

Elas não são rodapé, são parte do resultado.

- **Viés de acesso.** As bases só registram quem sabe que pode reclamar e consegue chegar ao canal.
- **Viés de canal.** Público mais velho reclama por telefone, público mais jovem por plataforma digital. Isso distorce o ranking de temas em direções opostas.
- **Viés de tema.** O Banco Central só contabiliza descumprimento de norma sob sua supervisão.
- **Conflito de modelo de negócio.** O Reclame Aqui vende serviços de reputação às empresas que avalia.
- **Demografia inexistente.** Nenhuma das três fontes publica idade, gênero ou região de quem reclama. Os perfis no dashboard vêm de dados de uso de crédito, o que é uma inferência de um passo.
- **Defasagem.** Cerca de 21 meses entre a camada demográfica (dez/2024) e o ranking mais recente (3º trimestre de 2026).
- **Janelas diferentes no Consumidor.gov.br.** Os indicadores por banco são de junho de 2026, os mais recentes publicados com índice de solução e nota para todos os grandes bancos. Julho e agosto têm volume, mas não o índice por empresa.
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
| Ranking do Banco Central | Trimestral, cerca de 3 semanas após o fechamento. A cada divulgação, refazer o teste de persistência com n igual a 15 |
| Consumidor.gov.br | Mensal |
| Reclame Aqui | Semestral |
| Relatório de Cidadania Financeira | Trienal. A edição mais recente, de abril de 2026, traz a base de dez/2024. Recalibrar o simulador quando sair base nova e medir o erro das projeções pré registradas quando o Banco Central publicar dados de dez/2025 |

Quando uma fonte publicar dado que contradiga o dashboard, a versão anterior não é apagada. O bloco de verificação registra o que mudou e o que foi descartado, para que a leitura antiga continue auditável.

## Histórico de versões

### v3, outubro de 2026

Redesenho da experiência e atualização dos dados.

**Experiência**
- De 11 para 5 abas. As três abas de fonte e o cruzamento viraram uma aba de Instituições; perfil de crédito e personas viraram uma aba só; simulador e projeções viraram a aba Modelos; validação, limitações e fontes viraram Metodologia.
- O caso Nubank, que aparecia em quatro lugares, ficou concentrado em um. Os vieses de cada fonte, antes repetidos em várias abas, viraram um quadro comparativo único na Visão geral.
- Tabelas técnicas recolhidas sob demanda, atalhos entre seções e achados com link para a aba que os comprova.
- Cada persona tem um botão que abre o simulador já preenchido com o perfil.
- Navegação funcional no celular, que não existia na v2.

**Dados**
- Ranking do Banco Central do 3º trimestre de 2026, com índices, reclamações procedentes e clientes das 15 instituições. O gráfico permite alternar entre o 1º e o 3º trimestre.
- Teste de persistência refeito com n igual a 15: o resultado passou de não significativo para confirmado.
- Consumidor.gov.br: indicadores de junho para seis bancos, que preenchem células antes marcadas como "sem dado", e volumes de julho e agosto.
- Reclame Aqui: janela de Nubank e Itaú atualizada para abril a setembro de 2026.

**Registro de verificação**
- O índice de solução do Santander no Consumidor.gov.br aparecia como 77,5% na v2, vindo de um comparativo anual. A v3 usa 16,4%, do recorte de junho que considera só os casos avaliados e é comum a todos os bancos. As duas medidas não foram reconciliadas, e a diferença está explicada no dashboard.
- A classificação do Itaú no cruzamento passou de "divergência parcial" para "oposição", e a do Santander de "convergência" para "divergência parcial", por causa dos novos dados do Consumidor.gov.br.

### v2

Camada preditiva: simulador de risco, projeções por modalidade e validação.

### v1

Leitura comparada das três fontes, cruzamento e personas.

## Aviso

Este material é para análise. Não é recomendação de banco, de produto financeiro ou de investimento.
