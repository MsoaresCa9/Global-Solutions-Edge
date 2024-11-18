# Global-Solutions-Edge
### Descrição do Projeto: Medidor de Mudanças Climáticas para Geração de Energia Renovável

#### Justificativa:
As mudanças climáticas têm um impacto direto sobre diversos sistemas de geração de energia renovável, como a solar e a eólica, que dependem de condições climáticas específicas para sua operação ideal. Por exemplo, a intensidade da luz solar e a velocidade do vento podem afetar significativamente a produção de energia dessas fontes renováveis. Este projeto tem como objetivo monitorar essas mudanças climáticas, mais especificamente a temperatura e a umidade do ambiente, utilizando sensores para coletar essas informações em tempo real. Os dados serão enviados a um servidor MQTT, permitindo o monitoramento contínuo e a análise dessas variáveis para entender melhor o impacto das condições climáticas sobre a geração de energia renovável.

### Descrição do Código

O código implementa a captura de dados de temperatura e umidade usando o sensor **DHT22** e transmite esses dados para um servidor MQTT, sempre que há uma mudança nas condições monitoradas. O funcionamento básico é o seguinte:

1. **Conexão Wi-Fi**: O dispositivo se conecta a uma rede Wi-Fi utilizando o módulo `network` do MicroPython, configurado com as credenciais da rede.

2. **Leitura dos Sensores**: Utiliza-se o sensor **DHT22** para medir a umidade e a temperatura do ambiente. As medições são feitas periodicamente.

3. **Detecção de Mudança Climática**: O sistema compara os valores atuais de temperatura e umidade com os valores anteriores. Se houver qualquer mudança nas leituras, o sistema publica as novas informações no servidor MQTT.

4. **Publicação no MQTT**: Quando ocorre uma mudança nos dados de temperatura ou umidade, essas informações são transformadas em uma mensagem JSON e enviadas para um servidor MQTT. O servidor MQTT, que é configurado com as credenciais fornecidas (endereço do broker, porta, usuário e senha), recebe os dados para posterior análise ou visualização em um sistema de monitoramento.

5. **Persistência e Notificação**: O servidor MQTT mantém as informações publicadas e pode ser utilizado para alertar ou registrar qualquer variação significativa nas condições climáticas, o que pode ser útil para a gestão de sistemas de energia renovável.

#### Componentes do Código:

- **Conexão Wi-Fi**:
  - O dispositivo se conecta à rede Wi-Fi configurada, garantindo que as medições possam ser enviadas para o servidor MQTT via internet.

- **Sensor DHT22**:
  - O sensor DHT22 é utilizado para medir a temperatura e a umidade do ar. Ele envia as leituras de temperatura em graus Celsius e a umidade relativa.

- **MQTT (Message Queuing Telemetry Transport)**:
  - O protocolo MQTT é utilizado para a comunicação entre o dispositivo e o servidor. O MQTT é ideal para este tipo de aplicação devido à sua leveza e eficiência, sendo amplamente utilizado em sistemas de Internet das Coisas (IoT) para enviar dados de forma rápida e confiável.
  - O código utiliza a biblioteca `umqtt.simple` para facilitar a conexão ao servidor MQTT e o envio de mensagens.
  - A comunicação é feita de forma segura, utilizando o protocolo SSL (com a biblioteca `ussl`) para garantir a criptografia das mensagens enviadas.

- **Biblioteca JSON**:
  - A biblioteca `ujson` é utilizada para formatar as leituras do sensor em um formato JSON, tornando os dados estruturados e fáceis de serem processados pelo servidor MQTT ou por outros sistemas que consumem essas informações.

- **Verificação de Mudanças**:
  - O código compara as leituras atuais de temperatura e umidade com as leituras anteriores. Caso haja alguma alteração, as novas informações são publicadas no servidor MQTT.

- **Execução em Loop**:
  - O código é executado em um loop infinito, verificando continuamente as condições climáticas e enviando as alterações para o servidor.

### Bibliotecas Necessárias

Para rodar este código, você precisará instalar as seguintes bibliotecas no seu dispositivo com MicroPython:

1. **`umqtt.simple`**:
   - Esta biblioteca é necessária para implementar o cliente MQTT, que permite enviar as mensagens para o servidor MQTT. Ela pode ser encontrada no repositório de bibliotecas do MicroPython.

2. **`dht`**:
   - A biblioteca `dht` é utilizada para controlar o sensor DHT22 e obter as medições de temperatura e umidade.

3. **`ujson`**:
   - A biblioteca `ujson` serve para serializar os dados em formato JSON, o que facilita o envio das informações de forma estruturada.

4. **`ussl`**:
   - Esta biblioteca é necessária para estabelecer conexões seguras (SSL/TLS) com o servidor MQTT, garantindo que os dados sejam enviados de forma criptografada e segura.

### Relação do Projeto com o Servidor MQTT

O servidor MQTT atua como o ponto central de comunicação entre o dispositivo e qualquer sistema que deseje monitorar as condições climáticas. 

- **Publicação de Dados**: O dispositivo coleta os dados dos sensores e publica essas informações no servidor MQTT utilizando tópicos específicos (neste caso, o tópico é "MQTT_weather"). Outros dispositivos ou aplicações podem então se inscrever nesse tópico para receber os dados em tempo real.
  
- **Monitoramento Contínuo**: O servidor MQTT pode ser configurado para armazenar os dados, processá-los e até enviar alertas em caso de variações significativas nas condições climáticas, o que é importante para a gestão de energia renovável. Por exemplo, se a temperatura ou umidade atingir valores críticos que possam impactar a eficiência dos sistemas solares ou eólicos, o sistema pode gerar alertas automáticos.

- **Escalabilidade**: A utilização do protocolo MQTT permite que esse sistema seja facilmente escalável. Caso o projeto evolua para monitorar outras variáveis climáticas ou para incluir mais sensores, o servidor MQTT pode gerenciar o tráfego de dados de múltiplos dispositivos simultaneamente.

### Demonstração do Projeto

Para ver o funcionamento do projeto em tempo real e acompanhar as medições de temperatura e umidade publicadas no servidor MQTT, você pode acessar a **demonstração online** através do seguinte link:

[**Demonstração do Projeto**](#) https://wokwi.com/projects/414925700008639489

### Integrantes do Projeto

Este projeto foi desenvolvido pelos seguintes integrantes:

- **Caio Soares Rossini** - RM555084
- **Lucas Serrano** - RM555170
- **Pedro Henrique Nobre** - RM557454

### Conclusão

Este projeto oferece uma solução prática e eficiente para monitorar as condições climáticas e entender como elas afetam a geração de energia renovável. A utilização do protocolo MQTT garante uma comunicação rápida, confiável e segura, permitindo que o sistema seja integrado facilmente a outros sistemas de monitoramento e análise de dados, facilitando a tomada de decisões no gerenciamento de fontes de energia renovável.
