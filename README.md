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

# Para um entendimento maior recomendamos: <br>
  https://fiapcom-my.sharepoint.com/:p:/g/personal/rm97956_fiap_com_br/EUcKIR1IkBtBspMGqecDNFQB0hZxeSfc6rCT5U1urutOqg?e=ONI4MX

  Safe Flood é um projeto criado com a intenção de ajudar a comunidade com enchentes.
Para isso, utilizaremos tanto IoT quanto Arduino. 
O IoT é uma tecnologia que envolve a interconexão de objetos físicos e dispositivos à Internet, permitindo a coleta, análise e compartilhamento de dados entre esses dispositivos. ​
Essa interconexão cria uma rede de dispositivos inteligentes que podem coletar informações do ambiente, trocar dados entre si e tomar ações automatizadas com base nos dados coletados. ​<br>
A importância da IoT reside em seu potencial para transformar diversos setores e melhorar a eficiência, a produtividade e a qualidade de vida.​
Como por exemplo a eficiência operacional, que permite o monitoramento em tempo real de processos e ativos, otimizando a eficiência operacional em indústrias, agricultura e logística.
<br>
A partir disso há os conceitos da IoT, como os:
- Dispositivos IoT: que são objetos físicos que podem ser sensores, atuadores, câmeras, veículos, eletrodomésticos e outros, conectados à Internet para coleta e troca de dados. 
-Sensores: que são dispositivos que coletam dados do ambiente, como temperatura, umidade, pressão, localização GPS, entre outros. 
- Atuadores: que são dispositivos que podem realizar ações com base nos dados recebidos, como ligar ou desligar um aparelho, abrir uma válvula, etc.
- Conectividade: é a capacidade de dispositivos se conectarem à Internet por meio de tecnologias como Wi-Fi, 4G/5G, Bluetooth, LoRa, Zigbee, entre outras.
- Cloud Computing: é a infraestrutura de servidores na nuvem onde os dados coletados são armazenados e processados.
- Big Data e Análise de Dados: é o processamento de grandes volumes de dados coletados pela IoT para obter insights e tomar decisões informadas.
- Automatização e Controle: é a capacidade de dispositivos IoT executarem ações automaticamente com base em condições predefinidas ou comandos de controle.
- Segurança: é a implementação de medidas de segurança para proteger dados e dispositivos contra ameaças cibernéticas.

Já a arquitetura da IoT envolve vários componentes interconectados para tornar tudo isso possível. Os principais componentes incluem:
1. Dispositivos IoT: São os sensores, atuadores e outros dispositivos conectados que coletam e transmitem dados.
2. Redes de Comunicação: Permitem que os dispositivos IoT transmitam dados para gateways ou diretamente para a nuvem. Isso pode ser feito via Wi-Fi, redes celulares, ou outras tecnologias.
3. Gateways: São dispositivos que atuam como intermediários entre os dispositivos IoT e a nuvem. Eles agregam dados, fazem pré-processamento e encaminham os dados para a nuvem.
4. Nuvem: A nuvem é onde os dados coletados são armazenados e processados. É aqui que ocorre a análise de dados, permitindo a extração de insights.
5. Aplicativos e Interfaces: Os aplicativos e interfaces de usuário permitem que os usuários interajam com os dispositivos IoT e acessem os dados e os insights gerados.
6. Segurança: A segurança é incorporada em todas as camadas da arquitetura para proteger os dispositivos, dados e comunicações.
<br>
Para a nossa tecnologia IoT funcionar, utilizamos o MQTT
 <br>Message Queuing Telemetry Transport ou MQTT é um protocolo de mensagens leve e eficiente projetado para comunicação entre dispositivos em redes de IoT. Ele foi desenvolvido com o objetivo de ser simples, rápido e confiável para a troca de dados em ambientes de baixa largura de banda, alta latência ou redes instáveis.
 <br>
O MQTT é amplamente utilizado na IoT devido à sua eficiência, escalabilidade e confiabilidade. Ele é adequado para uma variedade de casos de uso, desde monitoramento de sensores e automação residencial até aplicações industriais e de saúde. Além disso, muitas das principais plataformas de IoT suportam o MQTT como um dos protocolos de comunicação.
<br> <br>
A partir da teoria, nós utilizamos o Node-red como suporte entre as informações coletadas pelo site de clima (o Weather API) e a transmissão delas no Tago.Io . <br>
Nessa tela, estamos utilizando o nodered. Temos os nós que utilizamos e as suas ligações.  <br>
Ligamos o input, com o web request, com o json, com a função e a ligamos com o mqtt out e o debug.  <br>
No web request, colocamos em url o site que vamos pegar as informações. Como, estamos utilizando São Paulo como exemplo, no próprio url há a latitude e a longitude da cidade.  <br>
A função é onde especificamos quais informações nós queremos mostrar para o usuário. Como estamos lidando com enchentes, queremos mostrar as temperaturas - a atual, min e max-, a umidade do ar, a porcentagem de nuvens no céu e a velocidade dos ventos.  <br>
O mqtt out é a nossa ligação entre o node-red e o Tago.io, onde as informações serão mostradas.  <br>
Já o debug vai nos ajudar a conferir os dados, uma vez que mostra no próprio node-red as informações.  <br>
Para conseguirmos enviar os dados para o tago, precisamos criar um device mqtt. Depois entramos em general information para vermos o nosso token de segurança.  <br>
Voltamos para o nó de mqtt request no node-red e entramos em segurança, colando o nosso token ali. Assim, o node irá conectar com o tago.  <br>
Voltando no site do tago, entramos em emulator para colocarmos quais variáveis serão mostradas e depois utilizadas na criação de um dashboard.  <br>
Após essa etapa, entramos em Live Inspector, apontamos o play para que as informações apareçam.  <br>
Depois criamos um dashboard para mostrar visualmente as informações, selecionando o device que queremos e a variável escolhida. Nesse dashboard, escolhemos a variável nuvens.  <br>
Todo esse processo feito com o Weather API, também pode ser feito com o Arduino. No nosso projeto, o circuito do Arduino conta com o sensor de distância - o Ultrassônico, o sensor de temperatura e umidade - o DHT11, com leds verde, amarelo  e vermelho, e com um buzzer.  <br> 
O projeto Safe Flood agradece o interesse pelo funcionamento e aquisição de dados.


