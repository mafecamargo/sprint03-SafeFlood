# Sprint 03 - SafeFlood:
Para uma melhor compreensão do código, recomendamos visualizar primerio os seguintes branches: <br>
01- arduino <br>
02- function node-red <br>
03- function tago.io

Branch -> arduino: <br>
Código do Arduino UNO, com sensores de temperatura e umidade (DHT11), sensor de distância (Ultrassônico), leds coloridos (verde, amarelo e vermelho) e um buzzer. Nele estão incluidos as bibliotecas necessárias para acessar o DHT11 e para mandar as informações coletadas para o Node-red com a aplicação json.

Branch -> function node-red: <br>
Esse código cria as variáveis a partir do api original e elas serão apresentadas no tago.io. As variáveis são: temperatura (mostra, em °C, a termperatura atual), min (mostra, em °C, a temperatura mínima do dia), max (mostra, em °C, a temperatura máxima do dia), nuvens (mostra a porcentagem de nuvens no dia), umidade (mostra a porcentagem da umidade do dia), e vento (mostra, em m/s, a velocidade dos ventos naquele momento).

Branch -> function tago.io: <br>
Utilizando Json, esse código traz as variáveis necessárias para acessar as variáveis utilizadas no código no node-red. A partir delas, é possível visualizar as informações no Tago.io pelo Live Inspector, em forma de código, e de uma forma mais visual com a  criação de um dashboard.

Para um entendimento maior recomendamos: <br>
https://fiapcom-my.sharepoint.com/:p:/g/personal/rm97956_fiap_com_br/EUcKIR1IkBtBspMGqecDNFQB0hZxeSfc6rCT5U1urutOqg?e=ONI4MX
