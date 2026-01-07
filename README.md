# 🅿️ Sistema de Gerenciamento de Estacionamento com Cancela Automática

![Status](https://img.shields.io/badge/Status-Conclu%C3%ADdo-green)
![Arduino](https://img.shields.io/badge/Hardware-Arduino_UNO-blue)
![SENAI](https://img.shields.io/badge/Instituição-SENAI_SC-red)

## 📖 Sobre o Projeto

[cite_start]Este repositório contém o código-fonte e a documentação do **Sistema de Gerenciamento de Estacionamento com Cancela Automática**, desenvolvido como Trabalho de Situação de Aprendizagem para a UC de Internet das Coisas do curso **Técnico em Desenvolvimento de Sistemas** do SENAI Joinville[cite: 1, 2, 11].

O projeto consiste em um protótipo inteligente que gerencia o acesso a uma vaga de estacionamento. [cite_start]Diferente de cancelas comuns, este sistema utiliza lógica de estado para decidir se permite a entrada: a cancela só abre se um veículo for detectado na entrada **E** a vaga estiver livre[cite: 33, 38].

## ⚙️ Funcionalidades

* [cite_start]**Monitoramento de Vaga:** Um sensor monitora constantemente se a vaga está livre ou ocupada[cite: 37].
* [cite_start]**Controle de Acesso Inteligente:** A cancela permanece travada se a vaga estiver ocupada, mesmo que um carro se aproxime da entrada[cite: 39].
* **Feedback Visual e Sonoro:**
    * [cite_start]**Display LCD:** Exibe mensagens de status ("Vaga Livre", "Vaga Ocupada", "Bem-vindo", etc.)[cite: 48].
    * [cite_start]**Buzzer:** Emite sons distintos para sucesso (entrada liberada) e alerta (vaga ocupada)[cite: 39, 135, 151].
* [cite_start]**Automação:** Acionamento automático do servomotor simulando a cancela[cite: 47].

## 🛠️ Hardware e Componentes

[cite_start]A lista de materiais utilizada no protótipo inclui[cite: 52]:

* 1x Arduino UNO (Controlador principal)
* 2x Sensores Ultrassônicos HC-SR04 (1 para a cancela, 1 para a vaga)
* 1x Servomotor Micro Servo 9g (Cancela)
* 1x Display LCD I2C (Interface visual)
* 1x Buzzer Piezo (Interface sonora)
* Protoboard e Jumpers

## 🔌 Esquema de Ligação (Pinagem)

[cite_start]Abaixo está o mapeamento dos pinos conforme configurado no `sketch` do Arduino[cite: 59, 60, 61, 62, 64, 65]:

| Componente | Função | Pino Arduino |
| :--- | :--- | :--- |
| **Servo Motor** | Controle da Cancela | `D5` |
| **Buzzer** | Alerta Sonoro | `D9` |
| **Sensor 1 (Entrada)** | Trigger (Gatilho) | `D3` |
| **Sensor 1 (Entrada)** | Echo (Retorno) | `D2` |
| **Sensor 2 (Vaga)** | Trigger (Gatilho) | `D7` |
| **Sensor 2 (Vaga)** | Echo (Retorno) | `D6` |
| **Display LCD** | Comunicação I2C | `SDA` / `SCL` |

## 🧠 Como Funciona o Código

[cite_start]O sistema opera em loop verificando dois estados principais[cite: 101, 102, 118]:

1.  **Verificação da Vaga:** O sensor da vaga (Pinos 6 e 7) mede a distância. [cite_start]Se for menor que 50cm, o sistema define `vagaOcupada = true`[cite: 67, 109, 110].
2.  [cite_start]**Verificação de Entrada:** O sensor da entrada (Pinos 2 e 3) verifica se há um carro (distância < 100cm)[cite: 68, 125].
    * [cite_start]**Cenário A (Vaga Livre):** O display mostra "Bem-vindo", o buzzer toca (1000Hz) e o servo sobe para 90º[cite: 128, 135, 136].
    * [cite_start]**Cenário B (Vaga Ocupada):** O display avisa "Vaga Ocupada", o buzzer emite um som de alerta (400Hz) e o servo permanece fechado (0º)[cite: 144, 151].

## 👨‍💻 Autores

* [cite_start]**Kauan dos Anjos Vieira** [cite: 3, 8]
* [cite_start]**Matheus Etelvino dos Santos** [cite: 4, 9]

[cite_start]Orientador: Prof. Sergio Luiz da Silveira[cite: 31].

---
[cite_start]*Desenvolvido em Joinville/SC - 2025* [cite: 6, 7]
