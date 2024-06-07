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

Exato, na logica depois têm de pensar com microserviços 
Ou seja: 
 
1 Microserviço para ter os dados dos veículos (Tipo IMT - Com a matricula vais buscar o resto das info)
1 microserviço para detetar a entrada 
1 microserviço para detetar a saída (ou então juntar o de entrada e de saída)
1 microserviço para passar as multas
Cada microserviço tem de ser a sua própria BD   
E cada microserviço tem a sua responsabilidade, nada de misturas  

Ou seja, cada microserviço é uma "solution" / "projeto"

tem de correr de forma independente 
Ou seja, se um deles for abaixo, os outros não vão 

----Ou seja, por exemplo o pub microserviço é o que envia os dados de entrada e saida para um outro microserviço sub que verifica se passa do excesso de velocidade

Exato, contudo o mecanismo pub sub é o RabbitMQ que também tem o seu container no docker / podman

Portanto como "análise" seria colocarem o RabbitMq e mais dois microserviços a tentar comunicar entre eles 

Tecnologias a usar:
- Docker
- .NET
- Angular


RabbitMQ Comunicação entre Microservices:
https://learn.microsoft.com/en-us/dotnet/architecture/microservices/multi-container-microservice-net-applications/rabbitmq-event-bus-development-test-environment

![image](https://github.com/Gotcha-Project/.github/assets/97791234/649f7acf-a69c-40c9-a19c-b04ad2abf6e2)
