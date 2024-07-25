
### Repositório dos dados do Estudo

Para fins de reprodutibilidade dos resultados apresentados no estudo realizado, estão disponíveis aqui o conjunto de dados e os códigos-fonte dos scripts de análise e modelagem.

#### Descrição do Estudo

Estudo ecológico transversal com abordagem quantitativa aplicada e exploratória na investigação comparativa de **modelos de aprendizado de máquina** e modelagem da **estatística clássica**.

### Conjunto de Dados utilizado no Estudo

Conjunto de dados sobre registros diários de Crimes Violentos Letais e Intencionais (CVLI) ocorridos no Estado do Ceará, Brasil, no período de 2009 a 2023. Os indicadores de segurança pública CVLI incluem homicídio doloso, feminicídio, lesão corporal seguida de morte e latrocínio. Esses dados foram obtidos do portal da Secretaria da Segurança Pública e Defesa Social do Estado do Ceará [SSPDS-CE](https://www.sspds.ce.gov.br/indicadores-de-seguranca-publica/) disponíveis publicamente em formato XLSX.

#### Descrição dos Dados

O conjunto de dados coletado contém registros dos crimes, incluindo as seguintes variáveis originais:

```bash
RangeIndex: 53047 entries, 0 to 53046
Data columns (total 11 columns):
 #   Column                  Non-Null Count  Dtype
---  ------                  --------------  -----
 0   Município               53047 non-null  object
 1   AIS                     53047 non-null  object
 2   Natureza                53047 non-null  object
 3   Data                    53047 non-null  object
 4   Hora                    53047 non-null  object
 5   Dia da Semana           53047 non-null  object
 6   Meio Empregado          53047 non-null  object
 7   Gênero                  53047 non-null  object
 8   Idade da Vítima         53047 non-null  object
 9   Escolaridade da Vítima  53047 non-null  object
 10  Raça da Vítima          53047 non-null  object
dtypes: object(11)
memory usage: 4.5+ MB
```

- **Município**: Nome do município onde ocorreu o crime (variável categórica).
- **AIS**: Área Integrada de Segurança onde o crime foi registrado (variável categórica).
- **Natureza**: Tipo de crime (homicídio doloso, feminicídio, lesão corporal seguida de morte, roubo seguido de morte) (variável categórica).
- **Data**: Data do crime (variável de data).
- **Hora**: Hora do crime (variável de tempo).
- **Dia da Semana**: Dia da semana em que o crime ocorreu (variável categórica).
- **Meio Empregado**: Meio utilizado para cometer o crime (arma de fogo, arma branca, outros meios) (variável categórica).
- **Gênero**: Gênero da vítima (masculino, feminino, não informado) (variável categórica).
- **Idade da Vítima**: Idade da vítima em anos (variável numérica).
- **Escolaridade da Vítima**: Nível de escolaridade da vítima (variável categórica).
- **Raça da Vítima**: Raça da vítima (variável categórica).

#### Variáveis Adicionais

Durante a análise foram adicionadas outras variáveis para o *enriquecimento de dados*:

- **População**: População do município onde ocorreu o crime (variável numérica).
- **IDHM**: Índice de Desenvolvimento Humano Municipal (variável numérica).
- **PIB per Capita**: Produto Interno Bruto per capita do município (variável numérica).
- **Latitude**: Latitude geográfica do município (variável numérica).
- **Longitude**: Longitude geográfica do município (variável numérica).
- **DataHora**: Combinação da data e hora do crime.
- **Ano**: Ano em que o crime ocorreu.
- **Mês**: Mês em que o crime ocorreu.
- **Dia**: Dia do mês em que o crime ocorreu.
- **HoraTurno**: Hora do dia em formato de 24 horas.
- **Turno**: Período do dia em que o crime ocorreu (Manhã, Tarde, Noite, Madrugada).
- **Faixa Etária**: Faixa etária da vítima (0 a 14 anos, 15 a 19 anos, 20 a 59 anos, 60 anos ou mais).
- **População Alta**: Indicador binário se a população do município é alta (>200.000 habitantes).
- **IDHM Alto**: Indicador binário se o IDHM do município é alto (≥ 0.68).
- **Masculino**: Indicador binário se o gênero da vítima é masculino.
- **Feminino**: Indicador binário se o gênero da vítima é feminino.
- **Adolescente**: Indicador binário se a faixa etária da vítima é de 15 a 19 anos.
- **Homicídio Doloso**: Indicador binário se o crime foi homicídio doloso.
- **Capital Metropolitana**: Indicador binário se o município pertence à região metropolitana da capital.
- **Ano[2009-2023]**: Indicadores binários para cada ano (2009 a 2023).
- **Adolesc**: Indicador binário se a faixa etária da vítima é de 15 a 19 anos.
- **CapitalMetrop**: Indicador binário se o município pertence à região metropolitana.
- **MorteArmaFogo**: Indicador binário se a morte foi causada por arma de fogo.

#### Conjunto de Dados após o Feature Engineering
```bash
RangeIndex: 52911 entries, 0 to 52910
Data columns (total 48 columns):
 #   Column              Non-Null Count  Dtype
---  ------              --------------  -----
 0   Id                  52911 non-null  int64
 1   AIS                 52911 non-null  object
 2   Municipio           52911 non-null  object
 3   Natureza            52911 non-null  object
 4   Data                52911 non-null  object
 5   Hora                52911 non-null  object
 6   DiaSemana           52911 non-null  object
 7   MeioEmpregado       52911 non-null  object
 8   Genero              52911 non-null  object
 9   IdadeVitima         52911 non-null  int64
 10  EscolaridadeVitima  52911 non-null  object
 11  RacaVitima          52911 non-null  object
 12  DataHora            52911 non-null  object
 13  CVLI                52911 non-null  int64
 14  Ano                 52911 non-null  int64
 15  Mes                 52911 non-null  int64
 16  Dia                 52911 non-null  int64
 17  HoraTurno           52911 non-null  int64
 18  Turno               52911 non-null  object
 19  Ano2009             52911 non-null  int64
 20  Ano2010             52911 non-null  int64
 21  Ano2011             52911 non-null  int64
 22  Ano2012             52911 non-null  int64
 23  Ano2013             52911 non-null  int64
 24  Ano2014             52911 non-null  int64
 25  Ano2015             52911 non-null  int64
 26  Ano2016             52911 non-null  int64
 27  Ano2017             52911 non-null  int64
 28  Ano2018             52911 non-null  int64
 29  Ano2019             52911 non-null  int64
 30  Ano2020             52911 non-null  int64
 31  Ano2021             52911 non-null  int64
 32  Ano2022             52911 non-null  int64
 33  Ano2023             52911 non-null  int64
 34  PopulacaoAlta       52911 non-null  int64
 35  IdhmAlto            52911 non-null  int64
 36  Masculino           52911 non-null  int64
 37  Feminino            52911 non-null  int64
 38  Adolesc             52911 non-null  int64
 39  HomicidioDoloso     52911 non-null  int64
 40  CapitalMetrop       52911 non-null  int64
 41  FaixaEtaria         52911 non-null  object
 42  Populacao           52911 non-null  float64
 43  IDHM                52911 non-null  float64
 44  PIBPerCapita        52911 non-null  float64
 45  Latitude            52911 non-null  float64
 46  Longitude           52911 non-null  float64
 47  MorteArmaFogo       52911 non-null  int64
dtypes: float64(5), int64(30), object(13)
memory usage: 19.4+ MB
```

#### Referência

SSPDS Ceará (2024). Indicadores criminais dos anos anteriores. Crimes Violentos Letais Intencionais (CVLI) 2009-2023. Secretaria da Segurança Pública e Defesa Social do Estado do Ceará. Disponível em: [https://www.sspds.ce.gov.br/estatisticas-2-3/](https://www.sspds.ce.gov.br/estatisticas-2-3/)