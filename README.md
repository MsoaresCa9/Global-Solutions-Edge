Segue a atualização do README com o link da demonstração no Wokwi:  

---

# README - Projeto IoT com Sensor DHT22 e Comunicação MQTT  

## Descrição do Projeto  

Este projeto utiliza um microcontrolador com suporte a WiFi para capturar dados de temperatura e umidade utilizando o sensor DHT22 e publicá-los em um servidor MQTT. A aplicação é configurada para operar em uma rede WiFi específica, conectando-se a um broker MQTT para troca de mensagens. Os dados são enviados para tópicos dedicados, permitindo monitoramento remoto e integração com sistemas IoT.  

---

## Funcionalidades  

1. **Leitura do Sensor DHT22**  
   - Mede a **temperatura** (°C) e a **umidade relativa do ar** (%) em tempo real.  

2. **Conexão WiFi**  
   - Conecta-se automaticamente à rede WiFi configurada e mantém a conexão ativa.  

3. **Publicação em Tópicos MQTT**  
   - Publica os valores de temperatura e umidade em tópicos distintos no broker MQTT:  
     - **Umidade**: `/TEF/codetech/attrs/h`  
     - **Temperatura**: `/TEF/codetech/attrs/t`  

4. **Recepção de Mensagens MQTT**  
   - Inscreve-se em um tópico (`/TEF/codetech/cmd`) para processar mensagens recebidas do broker MQTT.  

5. **Reconexão Automática**  
   - Detecta e restaura conexões WiFi ou MQTT em caso de falhas.  

---

## Requisitos  

- **Hardware**:  
  - Microcontrolador com suporte a WiFi (ex.: ESP32 ou ESP8266)  
  - Sensor DHT22  
  - Conexões elétricas adequadas  

- **Bibliotecas Arduino**:  
  - **WiFi**: Conexão WiFi  
  - **PubSubClient**: Comunicação MQTT  
  - **DHT**: Leitura de dados do sensor  

---

## Configuração do Ambiente  

### 1. **Configuração WiFi**  
No código, substitua as seguintes variáveis pelas informações da sua rede WiFi:  
```cpp  
const char* SSID = "Wokwi-GUEST"; // Nome da rede WiFi  
const char* PASSWORD = "";        // Senha da rede  
```  

### 2. **Configuração do Broker MQTT**  
Configure o endereço e a porta do broker MQTT:  
```cpp  
const char* BROKER_MQTT = "23.22.163.175";  
int BROKER_PORT = 1883;  
```  

---

## Como Utilizar  

1. **Clone ou baixe o projeto para o seu ambiente de desenvolvimento Arduino.**  
2. **Instale as bibliotecas necessárias:**  
   - No Arduino IDE, vá em **Sketch -> Incluir Biblioteca -> Gerenciar Bibliotecas...** e instale as seguintes:  
     - `DHT sensor library`  
     - `PubSubClient`  
     - `WiFi`  

3. **Carregue o código no microcontrolador.**  
4. **Conecte o hardware corretamente:**  
   - O pino de dados do DHT22 deve ser conectado ao pino **D4** do microcontrolador.  

5. **Execute o programa e monitore os dados via monitor serial.**  

---

## Exemplo de Saída  

Monitor Serial:  
```plaintext  
------Conexao WI-FI------  
Conectando-se na rede: Wokwi-GUEST  
Conectado com sucesso na rede Wokwi-GUEST  
IP obtido: 192.168.0.10  

Umidade: 45.6% Temperatura: 23.7°C  

- Mensagem recebida: {"comando":"ligar"}  
```  

---

## Demonstrações  

- **Vídeo de Demonstração**: [https://youtu.be/X3XkPsLhWKg](https://youtu.be/X3XkPsLhWKg)  
- **Simulação Online no Wokwi**: [https://wokwi.com/projects/414925700008639489](https://wokwi.com/projects/414925700008639489)  

---

## Autores  

- **Caio Rossini**: RM555084  
- **Lucas Serrano**: RM555170  
- **Pedro Henrique Nobre**: RM557454  
