# Sprint 03 - SafeFlood:
Para uma melhor compreensão do código, recomendamos visualizar primerio os seguintes branches:
01- arduino
02- function node-red
03- function tago.io

Branch -> arduino:
Código do Arduino UNO, com sensores de temperatura e umidade (DHT11), sensor de distância (Ultrassônico), leds coloridos (verde, amarelo e vermelho) e um buzzer. Nele estão incluidos as bibliotecas necessárias para acessar o DHT11 e para mandar as informações coletadas para o Node-red com a aplicação json.

Branch -> function node-red:
Esse código cria as variáveis a partir do api original e elas serão apresentadas no tago.io. As variáveis são: temperatura (mostra, em °C, a termperatura atual), min (mostra, em °C, a temperatura mínima do dia), max (mostra, em °C, a temperatura máxima do dia), nuvens (mostra a porcentagem de nuvens no dia), umidade (mostra a porcentagem da umidade do dia), e vento (mostra, em m/s, a velocidade dos ventos naquele momento).

Branch -> function tago.io:
Utilizando Json, esse código traz as variáveis necessárias para acessar as variáveis utilizadas no código no node-red. A partir delas, é possível visualizar as informações no Tago.io pelo Live Inspector, em forma de código, e de uma forma mais visual com a  criação de um dashboard.
