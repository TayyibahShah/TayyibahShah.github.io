library(shiny)
library(ggplot2)
library(dplyr)
library(plotly)

library(readr)
alcoholdeath <- read_csv("alcoholdeaths2022.csv")

# Define UI
ui <- fluidPage(
  titlePanel("Alcohol-related deaths for males"),
  sidebarLayout(
    sidebarPanel(
      sliderInput("IMD_Quintile", "Select IMD Quintile:", min = 0, max = 5, value = c(0, 5))
    ),
    mainPanel(
      plotlyOutput("scatterplot")
    )
  )
)

# Define server logic
server <- function(input, output) {
  output$scatterplot <- renderPlotly(
    
    # Create the scatter plot with plot_ly
    p <- plot_ly(data = alcoholdeath, x = ~yeardeath, y = ~malesdeaths) %>%
      add_markers() %>%
      layout(title = "The number of male alcohol-related deaths from 2018 to 2022",
             xaxis = list(title = "Year of deaths registered"),
             yaxis = list(title = "Number of male deaths"),
             hoverlabel = list(bgcolor = "white", font = list(size = 12)),
             margin = list(l = 100, r = 100, b = 100, t = 100),
             legend = list(x = 0.9, y = 0.9), # Adjust legend position
    
    # Return the plotly object
    p
  ))}

# Run the application
shinyApp(ui = ui, server = server)

