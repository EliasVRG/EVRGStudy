# Conhecimentos obtidos em Scripts Python

## Importando Bibliotecas

- `pyautogui`: Para automação de tarefas no sistema operacional.
- `datetime`, `timedelta`: Para manipulação de datas e tempos.
- `pandas`: Para manipulação de dados tabulares.
- `tabulate`: Para formatar e exibir tabelas.
- `email.mime.multipart`, `email.mime.text`, `smtplib`: Para enviar e-mails.
- `ast`: Para manipulação de árvores sintáticas abstratas.
- `traceback`: Para exibir mensagens de erro detalhadas.
- `dotenv`: Para carregar variáveis de ambiente a partir de um arquivo `.env`.
- `sleep`: Para pausar a execução do programa.

## Definição de Funções

- `main()`: Função principal que coordena todo o processo.
- `define_execution_time(start_time, end_time)`: Função para calcular o tempo de execução.

## Inicialização e Configurações

- Carregamento de configurações universais a partir de um arquivo `.env`.
- Mapeamento dos nomes dos meses em inglês para português.
- Obtenção do nome do mês atual em inglês e sua tradução para português.
- Definição de caminhos para arquivos PDF com base na data atual.

## Leitura e Manipulação de PDFs

- Leitura e identificação de arquivos PDF em um diretório.
- Extração de dados de PDFs e conversão para DataFrame do Pandas.

## Consultas ao Banco de Dados Oracle

- Consulta de dados por ID.
- Consulta de guias baixadas.

## Manipulação de DataFrames

- Atualização de valores em um DataFrame com base em resultados de consultas.
- Concatenação de DataFrames.
- Remoção de linhas duplicadas.

## Interação com Interface Gráfica

- Automatização do preenchimento de formulários em uma aplicação.

## Envio de E-mails

- Envio de e-mails com base nos resultados obtidos.

## Tratamento de Exceções

- Tratamento de exceções e registro de erros em caso de falha na execução.

## Tempo de Execução

- Cálculo do tempo de execução do programa.


## Automação de Navegação Web e Download de Arquivos

### Bibliotecas Utilizadas:
- `playwright`: Utilizada para automatizar a navegação web e interagir com elementos da página.
- `time`: Utilizada para adicionar atrasos na execução do script.
- `re`: Utilizada para trabalhar com expressões regulares, permitindo a busca por padrões específicos no texto HTML.
- `os`: Utilizada para lidar com operações relacionadas ao sistema operacional, como salvar arquivos em um diretório específico.

### Funcionalidades:
1. **Inicialização do Navegador e Página Web:**
   - O script inicia um navegador Chromium headless usando o Playwright.
   - Em seguida, navega até a página de login de um site específico (`https://cn.vibraenergia.com.br/login/`).

2. **Autenticação:**
   - Preenche os campos de usuário e senha em campos específicos do formulário de login.
   - Realiza o login clicando no botão de acesso.

3. **Extração de URL:**
   - Extrai uma URL de uma página HTML específica.
   - Utiliza expressões regulares para localizar e extrair a URL de uma tag específica.

4. **Navegação e Interatividade:**
   - Navega para a URL extraída.
   - Interage com a página, clicando em elementos específicos.

5. **Preenchimento de Campos:**
   - Preenche campos de formulário com informações relevantes, como ano, código, etc.
   - Utiliza a biblioteca `pyautogui` para simular a digitação e pressionar teclas de tabulação e retorno.

6. **Download de Arquivos:**
   - Clica em um elemento específico para iniciar o download de um arquivo.
   - Utiliza a função `expect_download()` para esperar até que o download seja concluído.
   - Salva o arquivo baixado em um diretório específico, usando a função `save_as()`.

7. **Finalização do Navegador:**
   - Fecha o navegador após concluir todas as operações.

### Observações:
- O script demonstra um exemplo de automação de tarefas repetitivas em um navegador web, incluindo preenchimento de formulários, navegação e download de arquivos.
- É importante observar que a automação de navegação web deve ser realizada com cuidado para evitar violações de segurança e respeitar os termos de uso dos sites.


## Consulta a Bancos de Dados Oracle

### Bibliotecas Utilizadas:
- `oracledb`: Utilizada para conectar e interagir com bancos de dados Oracle.
- `datetime`: Utilizada para manipulação de datas e horas.
- `pandas`: Utilizada para manipulação e análise de dados tabulares.

### Funcionalidades:
1. **Consulta Básica:**
   - Realiza uma consulta a um banco de dados Oracle para recuperar informações específicas.
   - Utiliza o módulo `oracledb` para estabelecer uma conexão com o banco de dados.
   - Executa uma consulta SQL personalizada para buscar dados com base em critérios específicos.
   - Os resultados da consulta são processados e retornados como um objeto DataFrame do Pandas.
   - Os resultados são formatados conforme necessário, como a formatação da coluna de data.

2. **Consulta com Parâmetros:**
   - Aceita parâmetros adicionais para filtrar os resultados da consulta.
   - Os parâmetros são usados na cláusula WHERE da consulta SQL para restringir os resultados.

3. **Manipulação dos Resultados:**
   - Os resultados da consulta são recuperados e armazenados em um DataFrame do Pandas.
   - As colunas do DataFrame são renomeadas conforme necessário para melhor legibilidade.
   - Qualquer manipulação adicional dos dados pode ser realizada usando as funcionalidades do Pandas.

4. **Tratamento de Erros:**
   - O script inclui tratamento de exceções para lidar com erros potenciais durante a execução da consulta.
   - Em caso de erro, uma mensagem de erro é exibida, e o script retorna `None`.

### Observações:
- A biblioteca `oracledb` é específica para interação com bancos de dados Oracle e oferece uma interface simples para executar consultas SQL e recuperar resultados.
- O uso do Pandas permite uma manipulação fácil e eficiente dos dados recuperados da consulta, incluindo filtragem, ordenação e transformações.
- O tratamento de erros ajuda a garantir que o script possa lidar adequadamente com situações inesperadas, como falhas na conexão com o banco de dados ou consultas mal-sucedidas.

### PyInstaller:

O PyInstaller é uma ferramenta que permite converter scripts Python em executáveis independentes para várias plataformas, incluindo Windows, macOS e Linux. Ele é especialmente útil quando você deseja distribuir seu código Python para usuários que não têm Python instalado em seus sistemas.

Principais características do PyInstaller:

1. **Suporte Multiplataforma**: O PyInstaller é capaz de criar executáveis para Windows, macOS e Linux a partir do mesmo código-fonte Python.

2. **Empacotamento de Dependências**: Ele analisa automaticamente as dependências do seu projeto Python e as inclui no executável, facilitando a distribuição do software.

3. **Facilidade de Uso**: O processo de conversão de um script Python em um executável é simples e pode ser feito com apenas alguns comandos.

4. **Integração com Ambientes Virtuais**: O PyInstaller pode trabalhar com ambientes virtuais do Python, garantindo que as dependências do seu projeto sejam isoladas e incluídas corretamente no executável.

5. **Personalização Avançada**: Ele oferece várias opções para personalizar o processo de criação do executável, como a definição de ícones, descrições e outras propriedades do arquivo final.

### auto-py-to-exe:

O auto-py-to-exe é uma interface gráfica para o PyInstaller que simplifica ainda mais o processo de criação de executáveis a partir de scripts Python. Ele oferece uma experiência amigável ao usuário, permitindo que você converta seus scripts em executáveis com apenas alguns cliques.

Principais características do auto-py-to-exe:

1. **Interface Gráfica Intuitiva**: O auto-py-to-exe possui uma interface fácil de usar, com opções claras e simples para configurar o processo de criação do executável.

2. **Pré-configurações Personalizáveis**: Ele fornece várias pré-configurações que você pode ajustar de acordo com suas necessidades, como a inclusão de dependências adicionais, a definição de ícones e a escolha do modo de execução.

3. **Visualização do Script**: Antes de criar o executável, o auto-py-to-exe permite visualizar o código-fonte do script Python e fazer ajustes, se necessário.

4. **Compatibilidade com PyInstaller**: Por trás da interface gráfica, o auto-py-to-exe utiliza o PyInstaller para gerar os executáveis, garantindo a mesma funcionalidade e confiabilidade.

5. **Suporte da Comunidade**: O auto-py-to-exe é mantido por uma comunidade ativa e recebe atualizações regulares, o que significa que você pode obter suporte e novos recursos com frequência.

### Sobre a biblioteca Aspose.Cells

A biblioteca Aspose.Cells é uma ferramenta poderosa para trabalhar com planilhas do Excel em Python. Ela permite ler, escrever, modificar e formatar dados em arquivos do Excel, oferecendo uma ampla gama de funcionalidades para manipulação de planilhas.

No código fornecido, a biblioteca Aspose.Cells é utilizada para trabalhar com arquivos do Excel. Aqui está um resumo das principais funcionalidades do código:

1. **Leitura e Modificação de Planilhas**:
   - O código lê dados de planilhas Excel usando a classe `Workbook` da biblioteca Aspose.Cells.
   - Ele remove colunas indesejadas e formata os dados conforme necessário.

2. **Salvamento e Exclusão de Arquivos**:
   - Após a manipulação dos dados, o código salva as alterações em um novo arquivo usando o método `save` da classe `Workbook`.
   - O arquivo original é excluído do sistema de arquivos usando o módulo `os`.

3. **Manipulação de Dados**:
   - Os dados lidos das planilhas são processados e filtrados conforme as condições especificadas no código.
   - As operações incluem filtragem com base em valores específicos, formatação de datas e exclusão de colunas indesejadas.

4. **Integração com Outras Bibliotecas**:
   - O código utiliza outras bibliotecas Python, como `pandas`, `os` e `tabulate`, para realizar operações adicionais de processamento de dados e manipulação de arquivos.

Em resumo, a biblioteca Aspose.Cells oferece uma maneira eficaz e fácil de trabalhar com planilhas do Excel em Python, fornecendo uma ampla gama de recursos para criar, modificar e processar dados em arquivos do Excel.
