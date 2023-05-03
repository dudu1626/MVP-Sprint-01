# MVP-Sprint-01
Entregável da Sprint I: Análise de Dados e Boas Práticas - PUC-Rio

# Trabalho de análise dos acidentes ocorridos em um ano nas rodovias federais que foram registradas no Boletim de Acidente de Trânsito – BAT.<br>
Trabalho desenvolvido por: _Eduardo Ferreira Gonçalves_

---
<a name="motivacao"></a>
## 1. Motivação

O contexto que impulsionou a realização deste estudo se fundamenta na relevância do problema relacionado à segurança viária, atendimento pré-hospitalar, bem como em todas as consequências advindas dos acidentes registrados nas rodovias.<br>
O tema tratado está em grande destaque desde que a Organização Mundial da Saúde – OMS lançou dentro dos planos de Desenvolvimento Sustentável a Década de Ação pela Segurança no Trânsito 2021-2030 com ***a meta de prevenir ao menos 50% das mortes e lesões no trânsito até 2030***.<br>
Problemática que afeta o Brasil de maneira significativa, uma vez que, de acordo com a própria OMS e a Organização Pan-americana da Saúde - OPAS destacam que $\Large{93\%}$ das mortes no trânsito ocorrem em países de baixa e média renda, embora estes concentrem aproximadamente 60% dos veículos do mundo.
<br>
<img src="https://s2.glbimg.com/ebYLEvUR7eUIKICtOxJfniep6OI=/0x0:911x420/640x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_59edd422c0c84a879bd37670ae4f538a/internal_photos/bs/2022/L/1/SxdYbRQKCjEck8pSllBw/whatsapp-image-2022-10-01-at-15.59.36.jpeg" height="400" width="800">

---
<a name="objetivo"></a>
## 2. Objetivo

Com o foco principal nas consequencias físicas nas pessoas, este trabalho objetiva descrever e entender os acidentes veiculares ocorridos nas estradas federais do Brasil no ano de 2022 identificando as possíveis causas mais frequentes, o número de pessoas envolvidas e contabilizar consequências de danos físicos às pessoas (ferimento ou óbito), com isso, consubstanciar com dados os gestores públicos, que poderão tomar melhores decisões de implementação de políticas públicas para a prevenção de acidentes com fiscalização ostensiva e meios educacionais e otimizar a distribuição geográfica da estrutura estatal na fiscalização e no socorro.<br>
Mesmo sendo o foco uma análise criteriosa dos dados apresentados, srão feitas pequenas interrupções para demonstar onde seriam feitas as preparações (pré-processamento) dos dados para o treinamento de um 
**modelo de Machine Learning de aprendizagem supervisionada**.

---
<a name="problema"></a>
## 3. Tipo de Problema

Com os dados disponibilizados, há a possibilidade de, em tese, fazer modelos preditivos de regressão para inferir número de pessoas acidentadas de forma grave ou óbitos (aprendizado supervisionado), também sendo possível modelo não supervisionado na confecção de clusters das características dos acidentes estudados. Poderia ainda fazer modelos de previsão de séries temporais, como por exemplo ARIMA e SARIMA.

---
<a name="condicoes"></a>
## 4. Restrições e condições

Para o presente trabalho, decidiu-se como critério de seleção dos dados o ano mais recente que tivesse os 12 meses completos, ou seja, o ano de 2022.<br>
Das planilhas disponibilizadas, fez-se a escolha do arquivo que apresentava os dados agrupados por pessoa, com todas as causas e tipos de acidente. Disponível no [link](https://drive.google.com/file/d/1wskEgRC3ame7rncSDQ7qWhKsoKw1lohY/view).
<br>
<img src="https://raw.githubusercontent.com/dudu1626/datasets-publicos/main/imagens/prf-desenho.png" height="400" width="400">
<br>
Conforme o [site](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf) de dados abertos do Governo Federal, Os dados disponibilizados pela Polícia Rodoviária Federal – PRF são baseados no cadastro do Boletim de Acidente de Trânsito – BAT.
<br>
De acordo com a [Carta de serviços ao usuário 2022](https://drive.google.com/file/d/1nuKN2rMmPfmEwnGtI1Kw8M8zbWfhvZzU/view) para o acidente ser cadastrado no BAT, ele deve atender, pelo menos, uma das seguintes situações:
1. lesões em pessoas; 
2.	envolvimento de servidores da PRF, em serviço, independente da circunscrição; 
3.	danos a bens públicos não concedidos à iniciativa privada, tais como veículos, sinalização e mobiliário, entre outros; 
4.	danos ao meio ambiente; 
5.	condutor inabilitado, com Carteira Nacional de Habilitação (CNH) suspensa ou cassada (de forma administrativa ou judicial); 
6.	vazamento ou derramamento de produto perigoso; avaria nas embalagens dos produtos perigosos fracionados; dano no equipamento de transporte de produto perigoso a granel; 
7.	envolvimento de algum condutor que esteja sob influência de substância psicoativa de uso indevido (álcool ou qualquer outra), independentemente do teor ou da forma de constatação, bem como que tenha se recusado a se submeter a testes para a comprovação do uso de alguma dessas substâncias; 
8.	ocorrência de incêndio (abrangendo pelo menos um terço das dimensões em algum dos veículos envolvidos); 
9.	“veículo localizado” e “condutor não localizado” (depois de esgotadas as possibilidades de localização do condutor).<br>

---
<a name="dicionario"></a>
## 5. Dicionário dos dados

O dicionário para os dados utilizados na presente análise deveria estar disponível no [link](https://arquivos.prf.gov.br/arquivos/index.php/s/Qwxgt8T6grdiR03), mas após sucessivas tentativas de acesso sem sucesso, usou-se o Dicionário dos acidentes agrupados por ocorrência através do [site](https://drive.google.com/file/d/1dTuZVGmx4ui3VyGnKYztMHxcAAAdRUzq/view).<br>

Além dos atributos dispostos conforme o dicionário de dados, o dataset possui ainda os seguintes atributos referentes à administração da própria PRF, mas que não possuem detalhamento no dicionário, mas que pelo seu nome e durante a análise dos dados é possível inferir seu significado:
<br><br>
``'pesid', 'causa_principal', 'ordem_tipo_acidente', 'tipo_veiculo', 'marca', 'ano_fabricacao_veiculo', 'tipo_envolvido', 'estado_fisico', 'idade', 'sexo', 'regional', 'delegacia' e 'uop'.``
<br><br>

|**Nome da variável**|**Descrição**|
|:---|:---|
|id|Variável com valores numéricos, representando o identificador do acidente.|
|data_inversa|Data da ocorrência no formato dd/mm/aaaa.|
|dia_semana|Dia da semana da ocorrência. Ex.: Segunda, Terça, etc.|
|horario|Horário da ocorrência no formato hh:mm:ss.|
|uf|Unidade da Federação. Ex.: MG, PE, DF, etc.|
|br|Variável com valores numéricos representando o identificador da BR do acidente.|
|km|Identificação do quilômetro onde ocorreu o acidente, com valor mínimo de 0,1 km e com a casa decimal separada por ponto.|
|municipio|Nome do município de ocorrência do acidente.|
|causa_acidente|Identificação da causa presumível do acidente. Ex.: Falta de atenção, Velocidade incompatível, etc.|
|tipo_acidente|Identificação do tipo de acidente. Ex.: Colisão frontal, Saída de pista, etc.|
|classificação_acidente|Classificação quanto à gravidade do acidente: Sem Vítimas, Com Vítimas Feridas, Com Vítimas Fatais e Ignorado.	
|fase_dia|Fase do dia no momento do acidente. Ex. Amanhecer, Pleno dia, etc.|
|sentido_via|Sentido da via considerando o ponto de colisão: Crescente e decrescente.|
|condição_meteorologica|Condição meteorológica no momento do acidente: Céu claro, chuva, vento, etc.|
|tipo_pista|Tipo da pista considerando a quantidade de faixas: Dupla, simples ou múltipla.|
|tracado_via|Descrição do traçado da via: reta, curva ou cruzamento.|
|uso_solo|Descrição sobre as características do local do acidente: Urbano = Sim ou rural = Não.|
|latitude|Latitude do local do acidente em formato geodésico decimal|
|longitude|Longitude do local do acidente em formato geodésico decimal|
|pessoas|Total de pessoas envolvidas na ocorrência.|
|mortos|Total de pessoas mortas envolvidas na ocorrência.|
|feridos_leves|Total de pessoas com ferimentos leves envolvidas na ocorrência.|
|feridos_graves|Total de pessoas com ferimentos graves envolvidas na ocorrência.|
|ilesos|Total de pessoas ilesas envolvidas na ocorrência.|
|ignorados|Total de pessoas envolvidas na ocorrência e que não se soube o estado físico.|
|feridos|Total de pessoas feridas envolvidas na ocorrência (é a soma dos feridos leves com os graves).|
|veiculos|Total de veículos envolvidos na ocorrência.|

