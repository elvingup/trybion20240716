# DASHBOARD DAS VENDAS POR GERENTE

## MODELAGEM
pedidos [*] <<< [1] lojas
pedidos [*] <<< [1] calendario

## MEDIDAS 
### faturamento
faturamento = SUM(pedidos[valor_venda]) 
### qtde_pedidos
qtde_pedidos = COUNTROWS(pedidos) 
### ticket_medio
ticket_medio = DIVIDE([faturamento],[qtde_pedidos],"N/A") 

## DASHBOARD PAGE 

### Acompanhamento de vendas
*foto do gerente*
    visualizações 
        criar visual 
            gráfico de rosca
                legenda 
                    lojas[nome_loja]
                valores 
                    Medidas[faturamento] 
                manter todos os filtros 
        formatar visual 
            visual 
                legenda 
                    habilitada 
                    opções 
                        posição 
                            inferior central 
                fatias 
                    cores 
                        uma cor respectiva para cada loja 
                    espaçamento 
                        raio interno 
                            91% 
            geral 
                ícones de cabeçalho 
                    habilitado 
                dicas de ferramenta
                    habilitado 
*nome do gerente*
    visualizações 
        criar visual 
            score 
                campos 
                    Primeiro lojas[Gerente]     
                manter todos os filtros 
        formatar visual 
            visual 
                valor do balão 
                    fonte 
                        tamanho 26 
                    quebra de texto 
                        habilitado 
                    espaçamento de fonte 
                        habilitado 
            geral 
                ícones de cabeçalho
                    habilitado 
*filtro pelo nome*
    criar visual 
        segmentação de dados
            campos
                lojas[Gerente]
            manter todos os filtros 
    formatar visual 
        visual 
            configurações de segmentação 
                opções 
                    estilo 
                        bloco 
                seleção 
                    seleção múltipla com CTRL 
                        habilitado 
        geral 
            ícones de cabeçalho
                habilitado 

### Encontre as lojas da marca
visualizações 
    criar visual
        mapa 
            localização 
                lojas[nome_estado]
            dicas de ferramenta 
            Primeiro lojas[nome_loja]
        manter todos os filtros 
            habilitado 
    formatar visual
        visual 
            configurações do mapa
                estilo 
                    mostrar os rótulos 
                        habilitado 
                controles 
                    zoom automatico 
                        habilitado 
                    cultura de geocódigo
                        auto 
            bolhas 
                cores 
                    mostrar tudo 
                        habilitado 
        geral 
            efeitos 
                tela de fundo 
                    desabilitado 
            ícones de cabeçalho
                habilitado 
            dicas de ferramenta
                habilitado 

### Faturamento
visualizações 
    visual 
        score 
            campos 
                Medidas[faturamento]
        manter todos os filtros 
            habilitado 
    formatar visual 
        visual 
            valor do balão 
                fonte 
                    tamanho 22 
                exibir unidade 
                    auto
                quebra de texto
                    habilitado 
                espaçamento de fonte 
                    habilitado 
        geral 
            efeitos 
                tela de fundo 
                    desabilitado 
            ícones de cabeçalho 
                habilitado 

### Total de Pedidos
visualizações 
    visual 
        score 
            campos 
                Medidas[qtde_pedidos]
        manter todos os filtros 
            habilitado 
    formatar visual 
        visual 
            valor do balão 
                fonte 
                    tamanho 22 
                exibir unidade 
                    auto
                quebra de texto
                    habilitado 
                espaçamento de fonte 
                    habilitado 
        geral 
            efeitos 
                tela de fundo 
                    desabilitado 
            ícones de cabeçalho 
                habilitado 

### Ticket Médio
visualizações 
    visual 
        score 
            campos 
                Medidas[ticket_medio]
        manter todos os filtros 
            habilitado 
    formatar visual 
        visual 
            valor do balão 
                fonte 
                    tamanho 22 
                exibir unidade 
                    auto
                quebra de texto
                    habilitado 
                espaçamento de fonte 
                    habilitado 
        geral 
            efeitos 
                tela de fundo 
                    desabilitado 
            ícones de cabeçalho 
                habilitado 

### Faturamento por Período
visualizações
    criar visual 
        gráfico de colunas clusterizadas
            eixo X
                calendario[mes]
            eixo Y 
                Medidas[faturamento]
        manter todos os filtros 
            habilitado 
    formatar visual 
        visual
            eixo X 
                valores 
                    habilitado 
            eixo Y 
                valores 
                    habilitado 
                    exibir unidades 
                        Milhão 
            rótulos de dados 
                habilitado  
        geral 
            efeitos 
                tela de fundo 
                    desabilitado 
            ícones de cabaçalho 
            dicas de ferramentas 

### Detalhamento por Loja
visualizações
    criar visual 
        tabela 
            colunas 
                Loja
                    lojas[nome_loja]
                Faturamento 
                    Medidas[faturamento]
                Parcela Respectiva (%)
                    % do total geral para Medidas[faturamento]
                Análise por Período 
                    coluna Faturamento 
                        adicionar minigrafico 
                            eixo Y 
                                Medidas[faturamento]
                            eixo X 
                                calendar[mes]
                    Medidas[faturamento] por calendar[mes]
                    Mover para baixo 
        manter todos os filtros 
    formatar visual 
        visual 
            predefinições de estilo 
                estilo 
                    mínimo 
            grade 
                linhas de grade horizontais 
                    habilitado 
                linhas de grade verticais 
                    desabilitado 
                borda 
                    seção 
                        inferior 
            valores 
                fonte 
                    tamanho 9
                quebra de texto 
                    habilitado 
            cabeçalho de coluna
                fonte 
                    tamanho 9
                quebra de texto 
                    habilitado
            opções 
                largura de tamanho automático 
                    habilitado 
            totais 
                valores 
                    habilitado 
            coluna específica 
                série 
                    Loja 
                aplicar aos valores 
                    habilitado 
            minigráfico 
                aplicar configurações para minigrafico 
                    Análise por Período 
                minigráfico 
                    tipo 
                        linha 
                marcador 
                    mostrar 
                        Mais Alto 
                        Mais Baixo 
                        Isolado 
                    tamanho 3
        geral         
            título 
                desabilitado 
            efeitos 
                desabilitado 
            ícones de cabeçalho 
                habilitado 

## MOBILE PAGE 