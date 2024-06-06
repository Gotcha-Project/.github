## GOTCHA.

Uma ideia fixe que tinha inicialmente é a seguinte:
 
Temos uma auto estrada com controlo de velocidade média.
 
Existem 2 pontos de controlo: 1 de entrada e outro de saída 
Depois existe um serviço que lê os eventos enviados pelos pontos de entrada e saída, e verifica se a velocidade é a cima do limite 
 
Caso seja, manda para outro microserviço que trata de passar as multas e de enviar para o proprietário da viatura

Para isto é necessário usar um mecanismo de Pub/Sub (pub de publicar eventos - sub de subscrever para ficar à escuta e receber esses eventos)

A design pattern da aplicação é MediatR
E era um plus se conseguissem implementar isso.
é a design pattern que se usa para trabalhar com eventos

https://medium.com/@codebob75/rabbitmq-net-demo-publisher-subscriber-fanout-exchange-microservices-a414d8468f50