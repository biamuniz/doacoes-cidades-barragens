# O rompimento de uma barragem aumenta doações eleitorais ligadas à mineração?
Repositório para documentar o trabalho final da disciplina Métodos em Inferência Causal, do Master em Jornalismo de Dados, Automação e Data Storytelling do Insper.

## 1. Pergunta de pesquisa:
Considerando os acidentes em Mariana (2015) e Brumadinho (2019), o rompimento de uma barragem aumenta as doações eleitorais municipais de pessoas e empresas ligadas à atividade de mineração?

* Variável X: rompimento de barragem
* Variável Y: doação ligada à mineradora

Para o exercício de construção de variáveis e análises, fizemos uma investigação na base de receitas (doações) em 2012, 2016 e 2020.

## 2. Justificativa
Em novembro de 2015, a cidade de Mariana, em Minas Gerais, foi vítima de um dos maiores desastres ambientais com rejeitos do mundo. O rompimento da barragem do Fundão, das mineradoras Samarco, Vale e BHP Biliton, soterrou Bento Rodrigues,  matou, pelo menos 19 pessoas, deixou milhares de moradores sem água potável e impactou a fauna, flora e cursos d’água.

Até agora, a comunidade não foi reconstruída e os responsáveis não foram julgados.

Quase quatro anos mais tarde, Brumadinho, no mesmo Estado, foi varrida pelos rejeitos da barragem Mina Córrego do Feijão controlada pela Vale, causando a morte de 270 pessoas (oito delas ainda estão desaparecidas e o segundo maior desastre industrial do século.

Os dois acidentes, sem dúvida, mudaram tragicamente a dinâmica das cidades, impactando a economia local, pública e privada. Esta análise propõe tentar encontrar outras relações diretas entre as ocorrências e as eleições municipais. 
  
## 3. Metodologia e desenho de pesquisa
***3.1. Levantamento das cidades de interesse para a pesquisa: variável X***

De acordo com a nossa pergunta de pesquisa, focamos nos municípios com atividade mineradora em Minas Gerais. Para conseguirmos executar, fizemos mais um novo recorte, escolhendo as que possuíam barragens com risco severo de rompimento em 2019: são 8. Além de Mariana e Brumadinho, cidade onde aconteceram os acidentes, listamos Barão de Cocais, Catas Altas, Itabira, Nova Lima, Ouro Preto, São Gonçalo do Rio Abaixo.

Quando pensamos na pergunta de pesquisa, a variável X poderia ser uma marcação do ano da eleição posterior ao rompimento da barragem em cada cidade atingida, fazendo com que a linha doação na eleição da cidade tivesse a informação de forma booleana. 

***3.2.  Download das bases de dados***

Inicialmente, exportamos do [Repositório de Dados Eleitorais do Tribunal Superior Eleitoral](https://www.tse.jus.br/eleicoes/estatisticas/repositorio-de-dados-eleitorais-1) as bases de dados referentes às despesas e receitas das campanhas eleitorais municipais dos anos de 2012 (anterior ao rompimento das barragens), 2016 e 2020 (eleições após o rompimento) no estado de Minas Gerais.

***3.3. Tratamento das bases de dados***

Nesta etapa, filtramos os municípios de interesse do grupo: são 8 cidades onde barragens estavam com [risco iminente de rompimento em 2019](https://www.em.com.br/app/noticia/gerais/2019/02/12/interna_gerais,1030084/conheca-as-oito-barragens-mineiras-com-risco-severo-de-rompimento.shtml), ano anterior à última eleição municipal.

Além disso, padronizamos a escrita das variáveis que diferem em cada campanha eleitoral, transformamos o tipo da variável de valor da despesa e valor da receita.
Esta etapa foi distribuída entre os integrantes do grupo (cada membro tratou e analisou duas cidades selecionadas) inicialmente; no entanto, para a análise final, realizamos a união de todos os municípios selecionados.

***3.4. Acréscimo de bases complementares para análise***

Também foi feito download e adição de variáveis à nossa base de dados final com as 8 cidades. Foram acrescentados dados de PIB per capita, IDH-M e população de cada cidade, segundo o IBGE.

A intenção foi trazer contexto sobre as cidades a fim de poder comparar os dados de doações e encontrar indícios para facilitar a identificação de uma doação ligada à mineração, como por exemplo doações cujos valores são próximos ou ultrapassam o PIB per capita, além de outras proporcionalidades dos valores em relação a cada município, seu tamanho de população e  Índice de Desenvolvimento Humano.

***3.5. Análise exploratória e descritiva dos dados***

Para a análise exploratória dos dados, utilizamos a biblioteca Pandas, em Python. Calculamos valores descritivos, agrupados por candidatos, doadores, cidades e anos em busca de informações que pudessem ajudar a identificar uma doação ligada à mineração. O notebook está disponível neste [link](https://github.com/biamuniz/doacoes-cidades-barragens/blob/main/notebook-barragens.ipynb).

***3.6. Cruzamento jornalístico com informações da Receita Federal: a variável Y***

Com base na análise exploratória da etapa anterior, buscamos informações sobre os doadores mais expressivos das campanhas eleitorais nos dados de quadro societário da Receita Federal. Estas informações estão disponíveis na ferramenta CruzaGrafos, da Associação Brasileira de Jornalismo Investigativo (Abraji), por meio de consulta por nome ou CNPJ. 

Imaginamos que este trabalho poderia ser automatizado em um segundo momento se o CruzaGrafos lançar uma API do serviço, facilitando a construção da variável Y: uma coluna booleana indicando se a doação tem ligação com mineradoras.

## 4. Análise e discussão
A análise prévia dos dados de campanhas eleitorais pode contribuir para gerar ideias de pauta, antecipar problemas na apuração com os dados e sugerir linhas de investigação possíveis. No caso da nossa análise, foi possível retirar alguns insights e conclusões sobre o trabalho com dados de campanha, bem como direcionar a nossa busca em outras bases.

Encontramos doadores ligados às mineradoras que financiaram candidatos nas campanhas. Esse achado pode levar a questionamentos e pautas, como buscar de que forma essas empresas poderiam se beneficiar com a eleição daquele candidato (medidas de flexibilização na fiscalização, diminuição de impostos, por exemplo), qual a ligação do candidato com a atividade mineradora, quem são os sócios dessas empresas.

No entanto, a análise prévia sem um entendimento das bases e do contexto em que as cidades estão inseridas apresenta limitações para o trabalho jornalístico. Percebemos que um ponto de atenção é o tamanho dos arquivos do repositório do TSE, que dificulta a manipulação por editores de planilhas comuns. A falta de uma padronização das informações das bases de dados entre os anos também é um problema: encontramos, por exemplo, as grafias “Número UE” e “Sigla UE” se referindo a mesma variável, mas em anos diferentes. Isso colocou uma etapa adicional de tratamento das bases antes da análise.

As informações sobre os doadores ligados à mineração são limitadas, o que torna indispensável o cruzamento de dados sobre os CPFs e CNPJs doadores com ferramentas externas.

O entendimento do contexto da mineração nas cidades de Minas facilita o trabalho jornalístico com esses dados. Uma informação que apuramos, por exemplo, é a ligação de algumas pessoas com o sobrenome “Bethônico”, provavelmente do mesmo grupo familiar, na mineração. Logo, encontrar esse sobrenome na base disparava um alerta para investigação.

Mas o contexto não diz apenas sobre as cidades; devemos considerar também as particularidades das eleições. A partir do ano de 2014 a doação de pessoas jurídicas para campanhas eleitorais foi impedida. Saber disso é importante para não tomar conclusões “as empresas pararam de doar” ou “doações de pessoas físicas aumentaram nas campanhas de 2016 e 2020” como furos jornalísticos.

Para complementar a análise, criamos duas visualizações com a ferramenta flourish. A primeira mostra todas as [doações recebidas por candidatos nas oito cidades analisadas](https://public.flourish.studio/visualisation/8141049/); a segunda, destaca as [doações de mineradoras e pessoas relacionadas](https://public.flourish.studio/visualisation/8144466/) nas campanhas eleitorais.


***4.1 Anexo: Doações ligadas à mineração que encontramos na base***

***4.1.1 Itabira***
* Vinicius Alves Vieira De Souza e Mauricio Vieira De Souza	: Ambos doaram na campanha de Ronaldo Lage Magalhães em 2016 e são sócios de três empresas de mineração, de acordo com dados da Receita Federal: ERN Engenharia De Recursos Naturais Ltda, ERN Mineracao Ltda, ERN. As doações somaram R$99850,00. 
* Edwarde Jose Duarte: Doou para a campanha de Ronaldo Lage Magalhães em 2016. É sócio de várias empresas, entre elas, mineradoras: DPAR Holding Participacoes Ltda., Consorcio Mina Fabrica, Consorcio Mar Azul, Dpatri Holding Participacoes Ltda., Vemg Empreendimentos Imobiliarios S/A, Gran Park Sao Jose Ii Empreendimentos Imobiliarios S/A, Cmm - Consorcio Morro Da Mina, Skava-Minas Manutencoes E Locacoes Ltda, Skava Minas Mineracao, Construcoes E Transportes Ltda Scp, Consorcio Morro Do Ipe. 
* Belmonte Mineração: A mineradora doou 100 mil reais na campanha de Ronaldo Lage Magalhães em 2012.

***4.1.2 Barão de Cocais***
* Mineração Serras Do Oeste Ltda: A mineradora doou para a campanha de prefeito de Armando Verdolin Brandão do PSDB em 2012 o valor de R$ 40.000,00. Além disso, no mesmo ano a empresa doou para Sebastião Braz Brito, candidato a vereador pelo PTB o valor de R$ 2.500,00. Os valores da doação somam R$ 42.500,00.
* Arcelormittal Brasil S.A.: A mineradora doou para a campanha de prefeito de Armando Verdolin Brandão do PSDB em 2012 o valor de R$ 3.000,00.
* Rangel Almeida Bethonico, Minervino Almeida Bethonico e Diogo Villa Eboli Bethonico: Rangel e Minervino fizeram doações para todos os candidatos a prefeito em 2016. Para Armando Verdolin Brandão do PDT cada um doou o valor de R$ 5.000,00. Para Geraldo Abade Das Dores do PSDB cada um doou o valor de R$ 5.000,00. Para o candidato Décio Geraldo Dos Santos do PV apenas Minervino doou o valor de R$ 5.000,00. Para o candidato a vereador pelo PDT Sebastião Eustaquio Dos Santos, Rangel e Minervino doaram R$ 2.500,00 cada um. Os valores da doação em 2016 somam R$ 30.000,00. O sobrenome Bethonico volta a aparecer na eleição de 2020, também com doações para todos os candidatos. Rangel fez doações para Armando Verdolin Brandão do PDT no valor de R$ 50.000,00. Para Geraldo Abade Das Dores do PATRIOTA, Rangel e Minervino doaram cada o valor de R$ 25.000,00. Para o candidato Décio Geraldo Dos Santos do PSB, Rangel e Minervino doaram cada um o valor de R$ 134.750,00, enquanto Diogo doou o valor de R$ 26.609,89.
Diogo fez doações para dois candidatos a vereador na cidade, Sebastião Eustáquio Dos Santos (PDT) e  Marisa Cristina Lopes (PSB), no valor de R$ 10.000,00 para cada um.
O total de doações em 2020 dos Bethonico foi R$ 321.136,89.
O sobrenome Bethonico é bem conhecido na cidade de Barão de Cocais, são pessoas influentes e que têm muitos empreendimentos, dentre eles, a MR Mineração LTDA e a Mineração Fazenda Trindade LTDA. Em 2019 a empresa recebeu licença para expandir a mina, passando a produção de 300 mil toneladas/ano para 4,5 milhões de toneladas/ano (o que pode explicar o aumento das doações de 2016 para 2020).

* Jose Alcir Nunes: Doou para a campanha de Washington Seara de Freitas (AVANTE) em 2020 o valor de R$ 4.000,00. É executivo da ArcelorMittal.

***4.1.3 Mariana***
* Nilton José Teixeira Frade: Doou para a campanha de Duarte Eustáquio Gonçalves Júnior, PPS, em 2016, o valor de R$ 3.000,00. Nilton é sócio da NF Mineração, empresa que atua na cidade.

***4.1.4 Brumadinho***
* Helder Adriano Freitas: Doou para a campanha de Antonio Brandão (MDB) em 2020 o valor de R$ 50.000,00. Ele é sócio da HG Mineração LTDA, Onix Céu Aberto Mineração S/A e Minas Minério de Ferro S/A.

***4.1.5 Ouro Preto***
* Emterpel Empresa De Terraplenagem Pedrosa Ltda: A empresa doou para o candidato a prefeito Dimas Antônio Ferreira Dutra, do PL, em 2012 o valor de R$ 95.000,00.

***4.1.6 Nova Lima***
* Mineração Serras Do Oeste Ltda: A mineradora doou para a campanha a prefeito de Marcelino Antonio Edwirges do PT em 2012 o valor de R$ 100.000,00.
* Itabirito Mineração Ltda: A mineradora doou para a campanha de Vitor Penido de Barros do DEM o valor de R$ 376.000,00 em 2012.
* José Gregório Ferreira Da Mata: Doou para a campanha a vereador de Felipe Augusto Ferrarez da Mata (PP) em 2016 o valor de R$ 20.000,00. Ele é Direto na AngloGold Ashanti.
