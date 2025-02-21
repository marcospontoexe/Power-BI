# Power BI
O Power BI é uma ferramenta de Business Intelligence (BI) desenvolvida pela Microsoft, que permite analisar, visualizar e compartilhar dados de forma interativa. Ele é amplamente utilizado por empresas e profissionais para transformar grandes volumes de informações em relatórios e dashboards visuais que auxiliam na tomada de decisão.

Com o Powe BI é possível construir **dash board** através de **relatórios**

## Ambientes do power bi
O power bi disponibiliza três ambientes de trabalho; 
* **Exibição de relatórios**: Mostra os gráficos criados.
* **Exibição de tabelas**: Mostra as tabelas criadas.
* **Exibição de modelos**: Mostras o relacionamento criado entre as diversas tabelas criadas.

## Processo de criação de dash boards
1. Importar dados.
2. tratar os dados com o power query:
    * Remover colunas em branco
    * Remover linhas em branco: página inicial/reduzir linhas/remover linhas/remover linhas em branco.
    * Selecionar o tipo de dado correto para cada coluna (moeda, número, percental, data, texto...).
    * Segmentar os dados, dividir colunas: transformar/dividir coluna.
    * organizar em ordem cronológica (data, item, horário, valor...).
2. Relacionar as tabelas.
3. Criar fórmulas e equações para criação de indicadores.
    * Multiplicar valores: Selecione as colunas/adicionar coluna/padrão/multiplicação
    * Organizar a sequência de caracterres de uma coluna existente: Selecione a coluna/adicionar coluna/coluna de exemplo/ escreva a sequncia correta nas linhas da nova coluna.
    * Fórmulas DAX. 

4. Criar dash board. (pagina inicial/fechar e aplicar)
    * Listar os indicadores que você quer apresentar.
    1. Criar visual
        * Insirir as ferramentas visuais (gráfico, tabela...) no ambiente exibição de relatórios.
        * Gráfico de barras e funil: Para mostrar ranking,
        * Gráfico de colunas, linhas, área: Para mostar valores ao longo do tempo.
        * Gráfico de pizza ou rosca: Para mostar porcentagem de até 4 elementos no máximo, acima de 4 elementos o gráfico fica poluido visualmente.
        * Cartão: Para mostrar um único valor (faturamento, produto mais vendido, total de clientes...)
        * Indicador: Para mostrar porcentagem.
        * Gráfico de árvore hierarquica: Para representar cascata.
        * Segmentação de dados: Usado para filtrar dados (lista suspensa).
        * Arrastar a coluna desejada para dentro do campo do da ferramenta visual escolhida.
        * Somando os valores de uma coluna: dentro da aba "campo" escolha a operação de soma.
        * Para mostrar o item mais vendido: Filtros/ arraste a coluna que contem o nome dos itens para o campo "neste visual"/em "tipo de filtro" selecionar N superior/ em "mostrar itens selecione superior e o numero 1/em "por valor" selecione qual coluna usar para ranquear o item mais vendido (quantidade vendida)/aplicar filtro
    2. Fomartar visual
        * Para copiar a formatação de uma ferramenta ja existente para outra nova: selecione a ferramenta visual a ser copiada/página inicial/selecione o pincel/clique na nova ferramenta visual.

## Fórmulas DAX (Data Analysis Expression)
DAX são fórmulas prontas do Power BI, e algumas até lembram um pouco o Excel. Então com uma fórmula DAX você consegue somar valores (SUM), calcular a média de valores
(AVERAGE), contar (COUNT), e mito mais.

Para criar uma fórmula basta clicar com o botão direito em qualquer lugar da sua tabela e selecionar **nova medida**. Veja a baixo alguns exemplos:
1. Criar Medidas
    * São cálculos dinâmicos que dependem do contexto da visualização.
    * Exemplo; Soma de todas as vendas de uma determinada coluna: `Total Vendas = SUM(nome_da_tabela[nome_da_coluna])`.

2. Criar Colunas Calculadas
    * São adicionadas a uma tabela e armazenam valores fixos por linha.
    * Exemplo: `Preço Final = Tabela[Preço] * (1 - Tabela[Desconto])`.

3. Criar Tabelas Calculadas
    * Geram tabelas baseadas em cálculos, úteis para segmentação de dados.
    * Exemplo: `TabelaFiltrada = FILTER(Tabela, Tabela[Categoria] = "Eletrônicos")`.

4. Calculo entre equações DAX
    * Não precisa informar o nome da tabela, apenas o nome da função dax já criada.
    * Exemplo: `Qualidade = ([nome_equação_1]) / ([nome_equação_2] + [nome_equação_3])`


**Dica**: Aperte a tecla TAB para habilitar a fórmula depois de começar a digitar.
**Dica**: Para pular uma linha dentro da área para escrever a formula, aperte *shift* + *enter*.

Ao criar uma medida, a princípio, logo de cara, nada acontece. Mas vemos que
na lista de Campos são adicionadas novas informações, com um símbolo de
calculadora. Isso significa que acabamos de criar uma nova medida. Porém, só conseguimos
visualizar estes resultados no nosso relatório, colocando essas medidas em
algum gráfico.

### Funções de Agregação:
TotalVendas = SUM(Tabela[Vendas])
MédiaVendas = AVERAGE(Tabela[Vendas])
total de linhas da tabela = COUNTROWS(nome_da_tabela)

### Funções de Filtragem:
Permite usar filtros junto com as fórmulas: Nome_qualquer = CALCULATE(expressão(), condição_1(), condição_2(), condição_3()).
* Horas Produtivas = CALCULATE(SUM('BaseProdução'[Total Horas]), 'BaseProdução'[Ocorrência]=BLANK()). Para esse cálculo nós vamos fazer a soma de horas, mas filtrando
apenas as informações da coluna Ocorrência que são vazias (BLANK).
* Horas Paradas = CALCULATE(SUM('BaseProdução'[Total Horas]), 'BaseProdução'[Ocorrência]<>BLANK()): Para segundo cálculo nós vamos somar as horas, só que agora vamos filtrar
as informações da coluna Ocorrência que são diferentes de vazio (BLANK).

Vendas2024 = CALCULATE(SUM(Tabela[Vendas]), YEAR(Tabela[Data]) = 2024)

### Funções de Tempo (Time Intelligence):
VendasAnoPassado = CALCULATE(SUM(Tabela[Vendas]), PREVIOUSYEAR(Tabela[Data]))

### Funções Lógicas:
AltoDesempenho = IF(Tabela[Lucro] > 1000, "Bom", "Regular")

## Criando Tooltip (Dica de Ferramenta’)
O Tooltip é uma maneira de
detalhar ainda mais
uma informação de
um gráfico sem que
você precise alterar o seu Dashboard.

1. **crie uma nova página** para
que possamos criar um novo visual para a nossa
Tooltip. Dentro dessa nova página nós vamos fazer 2
configurações:
2. Habitie a nova página para funcionar como uma tooltip: Na aréa de ferramentas de visualização/Formato da página/ na área de `Informação da Página`/ habilitar a opção `permitir usar como dica de ferramenta`.
3. Tamanho da Página: ir até a guia Exibição/Exibição de página/ e selecionar a opção **Ajustar à Página**.
4. Crie as ferramentas visuais da página de tooltip, que apareceram quando selecionarmos uma passamos o mouse em uma ferramenta visual do dashboard.
5. Configurar para que essa Tooltip apareça dentro do dashboard ao passar o mouse em cima: Dentro clique na ferramenta visaul desejada/na área de ferramentas 
de visualização clique em **formatar visual**/geral/dicas de ferramenta/opções/página/escolha a página criada como tooltip.



