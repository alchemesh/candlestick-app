# Candlestick Pattern Application
Full Stack for the Candlestick app. 

This is the full stack deployment for the Candlestick Pattern application. Here you will find the complete Kubernetes deployment YAML file(s), along with easier deployment through Helm. There are complete installation instructions at the bottom so full free to jump there to get started. 

The Candlestick Pattern application was created to find candlestick patterns in the stock market. Traders use these patterns to predict where a particular security might go in the near to midterm future. Clearly, it can be a bit cumbersome to attempt to find these patterns in each stock manually day by day, and so with a small bit of code, this product was created to automate that process. 

Key featues about the app include:
* Many different patterns are tested
* There are several stocks to choose from for analysis
* Proccessing to results takes only a second
* Flexibility for scaling

This application was designed with an event-driven methodology in mind. There are 5 tiers to this application, with each tier having its own role to play as microservices for the application's bottomline. While it is not necessary to install each repository, I invite you to visit each tier for a better understanding of how each one functions.

The 5 tiers are:
1) FrontEnd (NodeJS):  Github Repository - [NodeJS Frontend](https://github.com/alchemesh/candlestick-frontend)
1) Message Broker (RabbitMQ)
1) Backend (Python):  Github Repository - [Python Backend](https://github.com/alchemesh/candlestick-backend)
1) API (Java):  Github Repository - [Java API](https://github.com/alchemesh/candlestick-java-api)
1) Database (MYSQL):  Github Repository - [MYSQL](https://github.com/alchemesh/candlestick-mysql)


***NOTE: The RabbitMQ broker service does not need a repository and can be deployed using the RabbitMQ Docker image***


## How it works ##

The first tier is the NodeJS frontend application which is simply a website. Once the user has made their choice, this kicks off the event. The event is popped onto the RabbitMQ message broker, which is then consumed by the Python backend. Data is extracted from YFinance for the chosen stock, it is then tranformed and loaded to the Java API. The Java API pushes the data to the MYSQL database. 

Afterwards, the NodeJS application transitions, and calls the Java API for data retrieval. The application graphs the chart, and attempts to find a pattern within the specified duration, which is 5 days. Results are displayed to the user, along with an explanation for the specific pattern if it is found. 


## How to use ##

Deploy the image using the Kubernetes deployment file that can be found in kubernetes/development. This file has all parts, including ingress, services, and deployments. The application stack can also be deployed using the Helm charts found in this repository. 

##### Using Kubernetes #####
kubectl apply -f kubernetes/deployment

or

##### Using Helm #####
helm install candlestick-app ./candlestick-app