# Candlestick Pattern Application
Full Stack for the Candlestick app. 

This is the full stack deployment for the Candlestick Pattern application. Here you will find the complete Kubernetes deployment YAML file(s), along with easier deployment through Helm. There are complete installation instructions at the bottom so full free to jump there to get started. 

The Candlestick Pattern application was created to find cnadlestick patterns in the stock market. Traders use these patterns to predict where a particular security might go in the near to midterm future. Clearly, it can be a bit cumbersome to attempt to find these patterns in each stock manually day by day, and so with a small bit of code, this product was created to automate that process. 

Key featues about the app include:
* Many different patterns are tested
* There are several stocks to choose from for analysis
* Proccessing to results takes only a second
* Flexibility for scaling

This application was designed with an event-driven methodology in mind. There are 5 tiers to this application, with each tier having its own role to play as microservices for the application's bottomline. 

The 5 tiers are:
1) FrontEnd (NodeJS)
1) Message Broker (RabbitMQ)
1) Backend (Python)
1) API (Java)
1) Database (MYSQL)
