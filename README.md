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
        * Gráfico de barras: Para mostrar ranking,
        * Gráfico de colunas, linhas, área: Para mostar valores ao longo do tempo.
        * Gráfico de pizza: Para mostar porcentagem de até 4 elementos no máximo, acima de 4 elementos o gráfico fica poluido visualmente.
        * Cartão: Para mostrar um único valor (faturamento, produto mais vendido, total de clientes...)
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

**Dica**: Aperte a tecla TAB para habilitar a fórmula depois de começar a digitar.

Ao criar uma medida, a princípio, logo de cara, nada acontece. Mas vemos que
na lista de Campos são adicionadas novas informações, com um símbolo de
calculadora. Isso significa que acabamos de criar uma nova medida. Porém, só conseguimos
visualizar estes resultados no nosso relatório, colocando essas medidas em
algum gráfico.







