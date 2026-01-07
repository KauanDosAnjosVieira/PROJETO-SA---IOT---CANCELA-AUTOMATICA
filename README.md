# 🅿️ Sistema de Gerenciamento de Estacionamento com Cancela Automática

![Status](https://img.shields.io/badge/Status-Conclu%C3%ADdo-green)
![Arduino](https://img.shields.io/badge/Hardware-Arduino_UNO-blue)
![SENAI](https://img.shields.io/badge/Instituição-SENAI_SC-red)

## 📖 Sobre o Projeto

Este repositório contém o código-fonte e a documentação do **Sistema de Gerenciamento de Estacionamento com Cancela Automática**, desenvolvido como Trabalho de Situação de Aprendizagem para a UC de Internet das Coisas do curso **Técnico em Desenvolvimento de Sistemas** do SENAI Joinville.

O projeto consiste em um protótipo inteligente que gerencia o acesso a uma vaga de estacionamento. Diferente de cancelas comuns, este sistema utiliza lógica de estado para decidir se permite a entrada: a cancela só abre se um veículo for detectado na entrada **E** a vaga estiver livre.

## ⚙️ Funcionalidades

* **Monitoramento de Vaga:** Um sensor monitora constantemente se a vaga está livre ou ocupada.
* **Controle de Acesso Inteligente:** A cancela permanece travada se a vaga estiver ocupada, mesmo que um carro se aproxime da entrada.
* **Feedback Visual e Sonoro:**
    * **Display LCD:** Exibe mensagens de status ("Vaga Livre", "Vaga Ocupada", "Bem-vindo", etc.).
    * **Buzzer:** Emite sons distintos para sucesso (entrada liberada) e alerta (vaga ocupada).
* **Automação:** Acionamento automático do servomotor simulando a cancela.

## 🛠️ Hardware e Componentes

A lista de materiais utilizada no protótipo inclui:

* 1x Arduino UNO (Controlador principal)
* 2x Sensores Ultrassônicos HC-SR04 (1 para a cancela, 1 para a vaga)
* 1x Servomotor Micro Servo 9g (Cancela)
* 1x Display LCD I2C (Interface visual)
* 1x Buzzer Piezo (Interface sonora)
* Protoboard e Jumpers

## 🔌 Esquema de Ligação (Pinagem)

Abaixo está o mapeamento dos pinos conforme configurado no `sketch` do Arduino:

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

O sistema opera em loop verificando dois estados principais baseados nas distâncias lidas pelos sensores:

1.  **Verificação da Vaga:** Considera a vaga ocupada se o objeto estiver a menos de **50cm**.
2.  **Verificação de Entrada:** Detecta a presença de um carro na entrada se o objeto estiver a menos de **100cm**.
    * **Cenário A (Vaga Livre):** O display mostra "Bem-vindo", o buzzer toca (1000Hz) e o servo sobe para 90º.
    * **Cenário B (Vaga Ocupada):** O display avisa "Vaga Ocupada", o buzzer emite um som de alerta (400Hz) e o servo permanece fechado (0º).

## 👨‍💻 Autores

* **Kauan dos Anjos Vieira**
* **Matheus Etelvino dos Santos**

Orientador: Prof. Sergio Luiz da Silveira.

---
*Desenvolvido em Joinville/SC - 2025*
