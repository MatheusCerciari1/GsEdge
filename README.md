#🧠 Sistema de Monitoramento de Fadiga e Postura
Saúde e bem-estar no ambiente de trabalho
#📋 Descrição do Projeto

O projeto propõe um sistema simples e acessível de monitoramento de fadiga e postura, voltado à saúde e bem-estar no ambiente de trabalho.

A solução simula o funcionamento de um sistema ergonômico inteligente, que detecta sinais de fadiga e alerta o usuário a realizar pausas inteligentes e corrigir a postura, prevenindo problemas físicos e melhorando a produtividade.

#⚙️ Funcionamento do Sistema

O sistema foi desenvolvido e simulado no Wokwi e integrado ao Node-RED, permitindo a visualização de dados e alertas em tempo real.

Um botão simula a detecção de fadiga.

Quando pressionado, o sistema:

Acende um LED indicador 💡

Emite um alerta sonoro 🔊 (buzzer)

Envia os dados para o Node-RED, registrando o alerta no dashboard.

Essas ações representam o momento em que o sistema detecta sinais de cansaço ou má postura e recomenda pausas.

#🧩 Tecnologias Utilizadas

Wokwi – Simulação do circuito eletrônico (sem uso físico de Arduino)

Node-RED – Simulação do fluxo de dados e exibição de dashboard

MQTT / HTTP – Comunicação entre o sistema físico simulado e o ambiente de visualização (Node-RED)

Arduino IDE / C++ – Lógica de programação embarcada

Dashboard Node-RED – Visualização de histórico e alertas

#📡 Comunicação MQTT / HTTP

A simulação no Node-RED representa o envio dos dados de forma HTTP (ou MQTT em projetos reais), simulando a transmissão de informações como:

fadiga_detectada: true

timestamp: 2025-11-11 10:45:00

alertas_totais: 7

Esses dados podem ser utilizados para gerar gráficos, contadores e estatísticas no dashboard.

#🧠 Explicação Técnica

O botão no circuito simula o sensor de fadiga (poderia ser substituído futuramente por sensores reais de movimento, piscar de olhos ou postura).

O LED indica visualmente o alerta de pausa.

O buzzer emite o som de aviso para o colaborador.

O Node-RED registra e exibe os dados em tempo real, mostrando o histórico de alertas emitidos.

#🖥️ Instruções de Uso e Replicação
1. Simulação no Wokwi

#Acesse o link do projeto no Wokwi:
👉 Wokwi - Sistema de Fadiga e Postura

Passos:

Clique em "Start Simulation".

Pressione o botão (que simula a fadiga).

Observe o LED acender e o buzzer emitir som.

Veja no Serial Monitor a mensagem de alerta.

2. Simulação no Node-RED

Importe o fluxo Node-RED no editor online.

Configure o Dashboard para exibir o número de alertas e o histórico.

Execute o fluxo e visualize os dados sendo atualizados a cada alerta.

#💡 Código-Fonte (Arduino)

Arquivo principal: monitor_fadiga.ino

#define BUTTON_PIN 15
#define LED_PIN 2
#define BUZZER_PIN 4

bool lastButtonState = HIGH;
unsigned long lastPressTime = 0;
const unsigned long pressCooldown = 5000; // 5 segundos entre alertas

void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUZZER_PIN, OUTPUT);
  Serial.begin(115200);
  Serial.println("Sistema de fadiga e postura iniciado");
}

void loop() {
  bool buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW && lastButtonState == HIGH) {
    unsigned long currentTime = millis();
    if (currentTime - lastPressTime > pressCooldown) {
      Serial.println("⚠️ Fadiga detectada!");
      digitalWrite(LED_PIN, HIGH);
      tone(BUZZER_PIN, 1000); // som audível
      delay(1500);
      noTone(BUZZER_PIN);
      digitalWrite(LED_PIN, LOW);
      lastPressTime = currentTime;
    }
  }

  lastButtonState = buttonState;
}

🧾 Integrantes
Nome	RM
Matheus Cerciari Reis	565817
Luis Gustavo Vasconcelos Costa	566023
🔗 Links Importantes

#🎥 Vídeo Explicativo: YouTube - Sistema de Fadiga e Postura

#💻 Simulação Wokwi: https://wokwi.com/projects/447335537270901761

#🩺 Impacto e Relevância

O sistema contribui diretamente para o tema “Saúde e bem-estar no trabalho”, abordando:

Ergonomia e conforto no ambiente de trabalho

Prevenção de fadiga e lesões por esforço repetitivo

Promoção de pausas inteligentes

Aumento da produtividade e qualidade de vida
