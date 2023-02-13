# Scripts-do-R (SHINY APP)

# Leitura de Base de Dados
biblioteca ( readr )
biblioteca ( readxl )

# Fazer Painel
biblioteca ( brilhante )
biblioteca ( painel brilhante )
biblioteca ( brilhanteauthr )
biblioteca ( brilhantejs )
biblioteca ( sódio )

# Manipulação de Dados
biblioteca ( arrumado )
biblioteca ( dplyr )
biblioteca ( magrittr )

# Fazer Gráficos
biblioteca ( ggplot2 )

# Incluir Temas no gráfico
biblioteca ( ggthemes )

# Fazer Mapas
biblioteca ( geobr )
biblioteca ( sf )
biblioteca ( tmap )
biblioteca ( folheto )

# Fazer gráficos Dinâmicos
biblioteca ( enredo )
biblioteca ( dygraphs )


# Fazer Tabelas Dinâmicas
biblioteca ( DT )
biblioteca( dados.tabela )
biblioteca ( reacionável )
biblioteca( caboExtra )
biblioteca ( gapminder )
biblioteca ( minigráfico )
biblioteca ( Hmisc )
biblioteca ( knitr )
biblioteca ( pastecs )
biblioteca ( gt )
biblioteca ( psicologia )

# Fazer Gráfico de Correlação
biblioteca( ggcorrplot )

# Trabalhe com html
biblioteca( htmltools )
biblioteca( htmlwidgets )

# Trabalhe com Markdown
biblioteca ( remarcação )
biblioteca ( rmarkdown )

# Personalização Visual
# biblioteca (fresco)
# ibrary(stargazer)


# Personalização Visual
# meu_tema <- create_theme(
#   adminlte_color(
#aqua=" #     0821F7",
#blue=" #     6573E5",
#     vermelho ="#ABB2ED",
#   ),
#     adminlte_sidebar(
#       dark_bg="#09DAF3"
#         ),
#     adminlte_global(
#       content_bg="#99DEE6"
#     )
#     )






# Criação dos Menus
ui  <- dashboardPage( title =  " Painel de Acidentes de Trânsito " , skin = " blue " ,
dashboardHeader( tags $ li(div(img( src = ' detran.jpeg ' ,
                altura  =  " 20px " ),
                estilo  =  " padding-top:12px; padding-right:200px; " ),
                classe  =  " lista suspensa " )
                title = " ANUÁRIO ESTATÍSTICO DE ÓBITO POR ACIDENTES DE TRÂNSITO " ,
                largura do título = 660 ,
                tags $ li( class  =  " suspenso " ,
                        tags $ style( " .main-header {max-height:50px} " ),
                        tags $ style( " .main-header .logo {altura:50px} " )
                ),
                tags $ li( class = " dropdown " , tags $ a( href = " https://www.detran.pa.gov.br " ,icon( " linkedin " ), " DETRAN-PA " , target = " _blank " )), tags $ li( class = " dropdown " , tags $ a( href = " https://github.com/MarioDhiego " ,ícone( "github " ), " AUTOR " , alvo = " _blank " )),
                dropdownMenu( tipo = " mensagens " ),
                dropdownMenu( type = " notificações " ),
                dropdownMenu( type = " tarefas " )
),
painelSidebar( largura = 200 ,
                 tags $ style( " .left-side, .main-sidebar {padding-center: 120px} " ),
  barra lateralMenu(
    menuItem( " ANUÁRIO "                        , tabName = " about1 " , icon = icon( " address-card " ),
            menuSubItem( " Sobre Anuário "       , tabName = " sobre1 " ),
            menuSubItem( " Pareamento de Dados " , tabName = " pareamento1 " )
             ),
    menuItem( " MICRODADOS "                     , tabName = " banco1 " , icon = icon( " database " ),
              menuSubItem( " Base de Dados "     , tabName = " base1 " ),
              menuSubItem( " Fonte de Dados "    , tabName = " fonte1 " ),
              menuSubItem( " Medidas "           , tabName = " medi1 " )),
    menuItem( " SOCIOECONÔMICO "                 , tabName = " socio1 " , icon = icon( " masculino " ),
             menuSubItem( " Gênero "             , tabName = " genero1 " ),
             menuSubItem( " Faixa Etaria "       , tabName = " idade1 " ),
             menuSubItem( " Raca "               , tabName = " raca1 " ),
             menuSubItem( " Escolaridade "       , tabName = " escola1 " ),
             menuSubItem( " Renda Familiar "     , tabName = " renda1 " ),
             menuSubItem( " Estado Civil "       , tabName = " civil1 " )),
    menuItem( " CONDIÇÃO DA VÍTIMA "           , tabName = " condicao1 " , icon = icon( " cadeira de rodas " ),
           menuSubItem( " Condição da Vítima " , tabName = " condi1 " ),
           menuSubItem( " Tipo da Vítimas "    , tabName = " tipo1 " ),
           menuSubItem( " Tipo de Acidente "   , tabName = " acid1 " ),
           menuSubItem( " Tipo de Veiculos "   , tabName = " veiculo1 " ),
           menuSubItem( " Efeito de Drogas "   , tabName = " droga1 " ),
           menuSubItem( " Efeito de Álcool "   , tabName = " álcool1 " )),
  menuItem( " OCORRÊNCIAS "                    , tabName = " calendario1 " , icon = icon( " calendar " ),
           menuSubItem( " Dias Semana "        , tabName = " dia1 " ),
           menuSubItem( " Meses "              , tabName = " mes1 " ),
           menuSubItem( " Ano "                , tabName = " ano1 " ),
           menuSubItem( " Turno "              , tabName = " turno1 " )),
  menuItem( " CUSTO HOSPITALAR "               , tabName = " custo1 " , icon  = icon( " hospital " ),
           menuSubItem( " Dias de Internação " , tabName = " dias1 " ),
           menuSubItem( " Custo de internacao " , tabName = " custo2 " )),
  menuItem( " MAPAS "                          , tabName = " mapa1 " , icon = icon( " globo " ),
           menuSubItem( " Belém "              , tabName = " bel1 " ),
           menuSubItem( " Municípios "         , tabName = " munic1 " ))
  )
  ),
painelCorpo(
#use_theme   (meu_tema),
  tabItems(
    tabItem( tabName = " sobre1 " ,
            fluidoLinha(
              coluna( largura = 8 ,
                     posição = " esquerda " ,
              tags $ img( src = " crime.jpeg " , largura = 600 , altura = 400 ),
              tags $ br() ,
              tags $ a( " Foto por Asdecom " ), align = " esquerda " ),
              coluna( largura = 4 ,
              tags $ br(),
              tags $ p( style = " text-align:justify;font-si20pt " ,strong( " ANUÁRIO ESTATÍSTICO DE ÓBITO POR ACIDENTE DE TRÂNSITO DO DETRAN-PA, É UM CATÁLOGO QUE ENGLOBA DADOS SOBRE AS CARACTERÍSTICAS DAS VÍTIMAS FATAIS, CUJO RESULTADO É UM PROCESSO DE GESTÃO E INTEGRAÇÃO DE MÚLTIPLAS BASES DE DADOS, UTILIZANDO O MÉTODO PRABABILÍSTICO DE RELACIONAMENTO DE REGISTROS DESENVOLVIDO POR FELLEGI E SUNTER(1969). " )),
              tags $ p( style = " text-align: justify;font-si20pt " ,strong( " PARA CRIAÇÃO DO ANUÁRIO EM FORMATO WEB, FOI CRIADO UM SCRIPT EM LINGUAGEM DE PROGRAMAÇÃO R-PROJECT VERSÃO 4.2.2 E UM AMBIENTE DE DESENVOLVIMENTO INTEGRADO (IDE) CHAMADO Rstudio VERSÃO 1.4.1.7 COM USO DE VÁRIOS PACOTES, PARA O AMBIENTE WINDOWS. " )),
              tags $ p( style = " text-align: justify;font-si20pt " ,strong( " O ANUÁRIO FOI CONSTRUÍDO EM ALINHAMENTO AO MANUAL DE GESTÃO DO RENAEST (RESOLUÇÃO DO CONTRAN Nº808/2020), UTILIZANDO METODOLOGIA FACTÍVEIS COM ESTATÍSTICAS DE TRÂNSITO PADRONIZADA PARA TODO O TERRITÓRIO NACIONAL, E AOS OBJETIVO DE DESENVOLVIMENTOS SUSTENTÁVEIS (RESOLUÇÃO DA ONU Nº70/2015). " ))
            )
            )
            ),
    tabItem( tabName = " pareamento1 " ),
    tabItem( tabName = " genero1 " ,
            fluidoLinha(
              box( largura = 6 ,
                  title = " Gênero das Vítimas " ,
                  estado = " principal " ,
                  solidHeader = TRUE ,
                  recolhível = TRUE ,
                  altura = 10 ,
                  plotlyOutput( " histograma1 " )
              ),
              box( largura = 6 ,
                title = " Estatística Resumo " ,
                estado = " principal " ,
                solidHeader = TRUE ,
                recolhível = TRUE ,
                altura = 10 ,
                verbatimTextOutput( " resumo1 " )
              )
            ),
    ),
    tabItem( tabName = " idade1 " ,
            fluidoLinha(
              box( largura = 7 ,
                  title = " Distribuição Etário das Vitimas Fatais " ,
                  estado = " principal " ,
                  solidHeader = TRUE ,
                  recolhível = TRUE ,
                  altura = 15 ,
                  plotlyOutput( " histograma2 " )
              ),
              caixa( largura = 5 ,
                  title = " Perfil Etário das Vitimas Fatais " ,
                  estado = " principal " ,
                  solidHeader = TRUE ,
                  recolhível = TRUE ,
                  altura = 12 ,
                  DT :: dataTableOutput( " abstratosidade " )
              )
            )
    ),
    tabItem( tabName = " raca1 " ,
            fluidoLinha(
              box( largura = 7 ,
                  title = " Raça das Vítimas " ,
                  estado = " principal " ,
                  solidHeader = TRUE ,
                  recolhível = TRUE ,
                  altura = 12 ,
                  plotlyOutput( " histograma3 " )
              )
            )
    ),
    tabItem( tabName = " escola1 " ,
            fluidoLinha(
              box( largura = 7 ,
                  title = " Grau de Escolaridade das Vítimas " ,
                  estado = " principal " ,
                  solidHeader = TRUE ,
                  recolhível = TRUE ,
                  altura = 12 ,
                  plotlyOutput( " histograma4 " )
              )
            )
    ),
    tabItem( tabName = " base1 " ,
            fluidoLinha(
              box( largura = 12 ,
                  title = " Conjunto de dados " ,
                  estado = " principal " ,
                  solideHeder = TRUE ,
                  recolhível = TRUE ,
                  altura = 35 ,
                  dataTableOutput( " tabela1 " )
              )
            )
    ),
    tabItem( tabName = " condi1 " ,
            fluidoLinha(
              box( largura = 7 ,
                  title = " Condição da Vitima " ,
                  estado = " principal " ,
                  solideHeder = TRUE ,
                  recolhível = TRUE ,
                  altura = 35 ,
                  plotlyOutput( " histograma5 " )
              )
            )
    ),
    tabItem( tabName = " civil1 " ,
            fluidoLinha(
              box( largura = 7 ,
                  titulo = " Estado Civil da Vitima " ,
                  estado = " principal " ,
                  solideHeder = TRUE ,
                  recolhível = TRUE ,
                  altura = 35 ,
                  plotlyOutput( " histograma6 " )
              )
            )
    )
    
    
    
    
    
    
    
)
)
)

servidor  <-  função ( entrada , saída , sessão ){


# -------------------------------------------------- -------------------------
# Gráfico 2 - Genero
output $ histograma1  <- renderPlotly({

# Definir diretório
setwd( " C:/Users/mario Dhiego/Documents/ENADE_2018_RMarkdown/Esqueleto_shiny/DashBoard1/Layout-DashBoard-em-Shiny " )

# Ler Base de Dados
Tabela_DT  <- read_excel( " Tabela_DT.xls " )
Tabela_DT $ Genero  =  fator ( Tabela_DT $ Genero ,
                          níveis = nomes(sort(tabela( Tabela_DT $ Genero ),
                                            diminuindo = VERDADEIRO )))  

g1  <- ggplot( Tabela_DT ) +
  aes( x = Genero ) +
  geom_bar( fill = " azul " ) +
labs( x = " Gênero " ,
      y = " Número de Vítimas " ,
      titulo = " Gráfico de Barras " ,
      legenda = " Fonte: Detran " ) +
  theme_gray() +
theme( plot.title = element_text( size = 12L , face = " bold " , hjust = 0.5 ),
       plot.caption = element_text( size = 10L , face = " bold " , hjust = 0 ),
       axis.title.y = element_text( size = 12L , face = " bold " ),
       axis.title.x = element_text( size = 12L , face = " bold " ),
       legend.position  =  " inferior " )
ggplotly( g1 )

# (tabela(Tabela_DT$Genero),
#         xlab="",
#         ylab="",
#         col="azul",
#         #xlim=c(0,300),
#         #ylim=c(0,300),
#         axis.lty="sólido",
#         lwd=2,
#         fonte=2,
#         main="Gráfico de Barras")

  })
# -------------------------------------------------- -------------------------



  
saída $ resumo1 <- renderPrint  ({
resumo( Tabela_DT $ Idade )
  })
  

output $ resumoidade  <-  DT :: renderDataTable({
   Descrição <- rbind (
                      " Vitimas Fatais " = NROW( Tabela_DT $ Idade ),
                      " Menor Idade " = min( Tabela_DT $ Idade ),
                      " Maior Idade " = max( Tabela_DT $ Idade ),
                      " Idade Média " = média( Tabela_DT $ Idade ),
                      " Idade Mediana " = mediana( Tabela_DT $ Idade ),
                      " 25/% Idades " = quantile( Tabela_DT $ Idade , probs  =  0.25 ),
                      " 75/% Idades " = quantile( Tabela_DT $ Idade , probs  =  0.75 )
  )
  colnames( Descritiva ) = " Estatísticas "
  datatable( Descritiva ,
            caption = ' Tabela 1: Perfil Etário das Vitimas Fatais. ' )
    
  
  
})


# Gráfico 2 - Idade
output $ histograma2  <- renderPlotly({
g2  <- ggplot( Tabela_DT , aes( x = Idade )) +
  geom_histogram( binwidth = 5 , col = " azul " ) +
  # geom_density(alpha=.2, fill="white")+
    labs( x = " Idade " ,
         y = " Número de Vítimas " ,
         title = " Vítimas Fatais por Acidentes de Trânsito " ,
         legenda = " Fonte: Detran " ) +
  theme_gray( base_size = 14 ) +
  theme( plot.title = element_text( size = 12L , face = " bold " , hjust = 0.5 ),
        plot.caption = element_text( size = 10L , face = " bold " , hjust = 0 ),
        axis.title.y = element_text( size = 12L , face = " bold " ),
        axis.title.x  = element_text( size = 12L , face = " bold " ))
ggplotly( g2 )

  # hist(Tabela_DT$Idade,
  #        col="azul",
  #        freq=T,
  #        xlab="Idades",
  #       ylab="Nº de Vítimas",
  #        border="preto",
  #        xlim=c(0,100),
  #        ylim=c(0,80),
  #        axis.lty="sólido",
  #        lwd=2,
  #        fonte=2,
         # probabilidade=VERDADEIRO,
  #       main="Vítimas Fatais p/ Acidentes de Trânsito",
         # sub="Fonte: Detran"
  #      )
    
  })


output $ histograma4  <- renderPlotly({
Tabela_DT $ Escolaridade  =  fator ( Tabela_DT $ Escolaridade ,
                          níveis = nomes(sort(tabela( Tabela_DT $ Escolaridade ),
                          diminuindo = VERDADEIRO )))  

g3  <- ggplot( Tabela_DT , aes( x = Escolaridade )) +
  geom_bar( fill = " azul " ) +
  labs( x = " Grau de Escolaridade " ,
       y = " Número de Vítimas " ,
       titulo = " Gráfico de Barras " ,
       legenda = " Fonte: Detran " ) +
  theme_gray() +
  theme( plot.title = element_text( size = 12L , face = " bold " , hjust = 0.5 ),
        plot.caption = element_text( size = 10L , face = " bold " , hjust = 0 ),
        axis.title.y = element_text( size = 12L , face = " bold " ),
        axis.title.x = element_text( size = 12L , face = " bold " ),
        legend.position  =  " inferior " )
ggplotly( g3 )


})



output $ histograma3  <- renderPlotly({
  Tabela_DT $ Raca  =  fator ( Tabela_DT $ Raca ,
                                  níveis = nomes(sort(tabela( Tabela_DT $ Raca ),
                                                    diminuindo = VERDADEIRO )))
  g4  <- ggplot( Tabela_DT , aes( x = Raça )) +
    geom_bar( fill = " azul " ) +
    labs( x = " Raça " ,
         y = " Número de Vítimas " ,
         titulo = " Gráfico de Barras " ,
         legenda = " Fonte: Detran " ) +
    theme_gray() +
    theme( plot.title = element_text( size = 12L , face = " bold " , hjust = 0.5 ),
          plot.caption = element_text( size = 10L , face = " bold " , hjust = 0 ),
          axis.title.y = element_text( size = 12L , face = " bold " ),
          axis.title.x = element_text( size = 12L , face = " bold " ),
          legend.position  =  " inferior " )
  ggplotly( g4 )
})


output $ histograma5  <- renderPlotly({
  Tabela_DT $ Condiçã o  =  fator ( Tabela_DT $ Condiçã o , _ _
                          níveis = nomes(sort(tabela( Tabela_DT $ Condiçã o ) ,
                                            diminuindo = VERDADEIRO )))
  g5  <- ggplot ( Tabela_DT , aes( x = Condiçã o )) +
    geom_bar( fill = " azul " ) +
    labs( x = " Condição da Vítima " ,
         y = " Número de Vítimas " ,
         titulo = " Gráfico de Barras " ,
         legenda = " Fonte: Detran " ) +
    theme_gray() +
    theme( plot.title = element_text( size = 12L , face = " bold " , hjust = 0.5 ),
          plot.caption = element_text( size = 10L , face = " bold " , hjust = 0 ),
          axis.title.y = element_text( size = 12L , face = " bold " ),
          axis.title.x = element_text( size = 12L , face = " bold " ),
          legend.position  =  " inferior " )
  ggplotly( g5 )
})



output $ histograma6  <- renderPlotly({
  Tabela_DT $ `Estado Civil`  =  fator ( Tabela_DT $ `Estado Civil` ,
                              níveis = nomes(sort(tabela( Tabela_DT $ `Estado Civil` ),
                                                diminuindo = VERDADEIRO )))
  g6  <- ggplot( Tabela_DT , aes( x = `Estado Civil` )) +
    geom_bar( fill = " azul " ) +
    labs( x = " Estado Civil da Vítima " ,
         y = " Número de Vítimas " ,
         titulo = " Gráfico de Barras " ,
         legenda = " Fonte: Detran " ) +
    theme_gray() +
    theme( plot.title = element_text( size = 12L , face = " bold " , hjust = 0.5 ),
          plot.caption = element_text( size = 10L , face = " bold " , hjust = 0 ),
          axis.title.y = element_text( size = 12L , face = " bold " ),
          axis.title.x = element_text( size = 12L , face = " bold " ),
          legend.position  =  " inferior " )
  ggplotly( g6 )
})









  
output $ tabela1  <- renderDataTable({
setwd( " C:/Users/mario Dhiego/Documents/ENADE_2018_RMarkdown/Esqueleto_shiny/DashBoard1/Layout-DashBoard-em-Shiny " )
  Tabela_DT  <- read_excel( " Tabela_DT.xls " )
  tabela de dados( Tabela_DT ,
            plug- ins = ' naturais ' ,
            extensões = ' Botões ' ,
            opções = lista ( dom = ' Blfrtip ' , botões = c( ' copiar ' , ' csv ' , ' excel ' , ' pdf ' , ' imprimir ' ),
                           engthMenu = lista (c( 5 , 50 , 100 , 250 , - 1 )), c( 5 , 50 , 100 , 250 , " Todos " ),
                           comprimento da página = 5 ,
                           Largura automática = VERDADEIRO ,
                           scrollX = TRUE ),
          nomes de linha = FALSE ,
          class = ' cell-border compact stripe hover linha-border order-column dt-body-right ' ,
          estilo = ' bootstrap ' ,
          editável = ' célula ' ,
          colnames = c( ' Gênero ' , ' Idade ' , ' Raça ' , ' Estado Civil ' , ' Escolaridade ' , ' Condição ' , ' Tipo ' , ' Turno ' , ' Bairro ' , ' Municípios ' ),
          caption = ' Base de Dados sobre Vitimas Fatais por Acidentes de Trânsito-2020. ' )
  })

# output$regressao1 <- renderPrint({
#   model1 <- lm(mpg~am,data=mtcars)
#   model2 <- lm(mpg~am + wt + hp,data=mtcars)
#   modelo1 <- stargazer(model1,model2,digits=4, type = "html", header = FALSE)
# })
    
    
    
  

  
  
  
  
}





shinyApp( interface do usuário , servidor )
