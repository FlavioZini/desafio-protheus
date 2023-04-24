# desafio-protheus

1. Instala o pacote FPDF no ambiente Python. O FPDF é um pacote para criação de documentos PDF em Python. Com ele, é possível criar documentos PDF programaticamente, adicionando textos, imagens e tabelas, por exemplo.

![image](https://user-images.githubusercontent.com/130913679/234136322-daeee4d7-d327-4b85-b10f-8df9bd1ab206.png)

2. Esse trecho de código importa as bibliotecas necessárias para o projeto:

-> sqlite3: biblioteca para trabalhar com banco de dados SQLite;
-> requests: biblioteca para fazer requisições HTTP;
-> json: biblioteca para trabalhar com JSON;
-> datetime: biblioteca para trabalhar com datas e horários;
-> fpdf: biblioteca para criar arquivos PDF.

![image](https://user-images.githubusercontent.com/130913679/234136232-09d934fa-9275-444e-afa0-b8009c010816.png)

3. Essa parte do código cria uma conexão com o banco de dados desafio_protheus.bd e cria duas tabelas: Acao e Cotacao.

A tabela Acao possui três colunas: idAcao, simbolo e nome. A coluna idAcao é uma chave primária que identifica exclusivamente cada ação, enquanto as colunas simbolo e nome armazenam o símbolo e o nome da ação, respectivamente.

A tabela Cotacao possui sete colunas: idAcao, idCotacao, Cotacao, ValorMercado, VolumeTransacoes, Moeda e Data. A coluna idCotacao é uma chave primária que identifica exclusivamente cada registro de cotação, enquanto a coluna idAcao é uma chave estrangeira que relaciona cada cotação com uma ação. As colunas Cotacao, ValorMercado, VolumeTransacoes, Moeda e Data armazenam os valores correspondentes à cotação da ação no momento específico.

![image](https://user-images.githubusercontent.com/130913679/234136351-cd55cb3d-e6cd-4878-abc2-9ec977fab34f.png)

4. Essa parte do código faz o download de uma lista de siglas de ações disponíveis a partir de uma API (https://brapi.dev/api/available) e armazena essas siglas em um arquivo JSON chamado "siglas.json". O objetivo é obter as siglas para depois fazer consultas de cotações das ações utilizando outras APIs.

O processo consiste em fazer uma solicitação GET para a API, verificar se a resposta foi bem-sucedida, converter a resposta para um objeto Python, criar um objeto Python com as siglas e escrever o objeto Python em um arquivo JSON. Ao final, imprime uma mensagem indicando que as siglas foram armazenadas com sucesso.

![image](https://user-images.githubusercontent.com/130913679/234136397-5bccea6d-07f0-4930-8ddc-c160730b56ff.png)

5. Essa parte do código é responsável por fazer uma solicitação GET para a API da brapi.dev para cada sigla presente no arquivo siglas.json. Se a resposta da API retornar um status_code igual a 200, os dados da cotação são extraídos da resposta JSON e inseridos no banco de dados usando a função inserir_cotacao_bd(). Se o status_code não for 200, uma mensagem de erro é exibida informando que houve um problema ao consultar a sigla correspondente.

![image](https://user-images.githubusercontent.com/130913679/234136735-1014c9b9-7471-4119-a11d-d3e4f5309c18.png)
![image](https://user-images.githubusercontent.com/130913679/234136807-c19a0195-37cd-4dc4-8050-091c503d4108.png)

6. Esta etapa cria um arquivo PDF chamado "dados.pdf" e adiciona uma página a ele. Em seguida, busca os dados do banco de dados criado anteriormente, percorre os resultados da consulta e adiciona as informações de cada ação em linhas separadas. As informações incluem o símbolo da ação, o nome, a cotação, o valor de mercado, o volume de transações, a moeda e a data. Depois de adicionar todas as informações, o PDF é salvo e fechado.

![image](https://user-images.githubusercontent.com/130913679/234136863-0dd924ec-1007-4250-a1e5-23eafd1e071e.png)
