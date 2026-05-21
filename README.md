# Sprint-Computer-Organization-and-Architecture

# Módulo de Controle Otimizado em Baixo Nível para Eletropostos

## Integrantes

- João Pedro Santos Ferreira — RM: 569202  
- Maria Beatriz Braga de Lima — RM: 570501  
- Ulysses Gomes Soares de Souza — RM: 573826  
- Yasmin Cristina Carvalho Mayer — RM: 573964  

---

# Problema

Os eletropostos modernos utilizam softwares desenvolvidos em linguagens de alto nível e hardwares genéricos, o que pode causar desperdício de recursos computacionais e maior consumo energético.

Processos como autenticação de usuários, leitura de sensores e controle de carga elétrica são executados continuamente, aumentando o uso da CPU e o consumo de energia do sistema.

Além disso, sistemas pouco otimizados podem gerar:

- Maior consumo elétrico  
- Baixa eficiência computacional  
- Maior latência nas operações  
- Desperdício de recursos embarcados  
- Necessidade de hardware mais potente  

---

# Justificativa

Com o crescimento da mobilidade elétrica e dos veículos sustentáveis, os eletropostos passaram a ter um papel importante no consumo energético urbano.

Nesse cenário, reduzir o consumo computacional dos sistemas embarcados pode contribuir diretamente para:

- Melhor eficiência energética  
- Menor desperdício de energia  
- Melhor aproveitamento de energias renováveis  
- Redução do custo operacional  
- Maior desempenho do sistema  

A utilização de programação em baixo nível (Assembly) e arquiteturas eficientes como RISC-V permite desenvolver sistemas mais rápidos, leves e econômicos.

---

# Proposta de Solução

O projeto propõe o desenvolvimento de um módulo de controle otimizado em baixo nível para eletropostos.

A solução utiliza Assembly e conceitos de arquitetura de computadores para reduzir o número de instruções executadas pelo processador, diminuindo o consumo energético e aumentando a eficiência do sistema.

O módulo é responsável por:

- Gerenciar leitura de sensores  
- Controlar corrente e tensão da recarga  
- Realizar autenticação de usuários  
- Monitorar consumo energético  
- Operar com baixa latência  
- Minimizar ciclos de clock  

O sistema foi projetado para funcionar em microcontroladores e sistemas embarcados de baixo consumo.

---

# Objetivos do Projeto

- Reduzir o consumo energético computacional dos eletropostos  
- Melhorar a eficiência de sistemas embarcados  
- Aplicar conceitos de arquitetura de computadores  
- Utilizar programação em baixo nível (Assembly)  
- Demonstrar otimizações relacionadas a pipeline, cache e ciclos de clock  
- Relacionar eficiência computacional com sustentabilidade energética  

---

# Arquitetura do Sistema

## Fluxo do Sistema

Inicialização  
↓  
Autenticação do usuário  
↓  
Verificação do veículo  
↓  
Leitura dos sensores  
↓  
Controle da carga  
↓  
Monitoramento contínuo  
↓  
Desligamento seguro  

---

# Camada de Hardware

## Sensores

- Sensor de corrente  
- Sensor de tensão  
- Sensor de temperatura  
- Detector de conexão do veículo  

## Atuadores

- Relé de potência  
- PWM para controle da carga  
- LEDs e buzzer de status  

## Arquiteturas Utilizadas

- RISC-V  
- MIPS  
- x86  
- ARM Cortex-M  

---

# Organização do Software

## Sensor Manager

Responsável pela leitura contínua dos sensores.

## Charge Controller

Controla a potência e o fluxo de energia da recarga.

## Auth Module

Realiza autenticação de usuários via RFID ou cartão.

## Energy Monitor

Monitora o consumo energético do sistema.

## Safety Module

Detecta sobrecorrente, superaquecimento e falhas.

---

# Conceitos de Arquitetura Aplicados

## Arquitetura RISC

A arquitetura RISC utiliza instruções simples e rápidas, reduzindo o número de ciclos necessários para executar tarefas.

Isso proporciona:

- Menor consumo energético  
- Melhor eficiência computacional  
- Menor uso de hardware  
- Maior desempenho em sistemas embarcados  

---

## Comparação entre RISC e CISC

| RISC | CISC |
|---|---|
| Instruções simples | Instruções complexas |
| Menor consumo energético | Maior consumo |
| Execução rápida | Maior complexidade |
| Ideal para embarcados | Mais comum em desktops |

O projeto utiliza conceitos da arquitetura RISC devido à sua eficiência energética e melhor desempenho em sistemas embarcados.

---

## Pipeline

O pipeline permite executar múltiplas etapas de instruções simultaneamente, aumentando o desempenho do processador.

### Exemplo:

```asm
LW R1, 0(R2)
ADD R5, R6, R7
ADD R3, R1, R4
```

Com pipeline, o processador consegue buscar, decodificar e executar instruções em paralelo, reduzindo o tempo total de processamento.

### Benefícios do Pipeline

- Maior throughput  
- Melhor aproveitamento da CPU  
- Redução de tempo de execução  
- Menor consumo energético por operação  

---

## Cache

O uso eficiente da memória cache reduz acessos desnecessários à memória principal.

Estratégias utilizadas:

- Buffer circular  
- Dados alinhados  
- Minimização de cache misses  
- Redução de acessos aleatórios  

Isso melhora o desempenho e reduz o consumo energético do sistema.

---

## Ciclos de Clock

O projeto busca reduzir o CPI (Cycles Per Instruction), aumentando a eficiência do processador.

Objetivos:

- Maximizar throughput  
- Minimizar latência  
- Reduzir consumo energético por instrução  
- Melhorar resposta em tempo real  

---

# Exemplo de Código Assembly (MIPS)

```asm
.data
sensor_addr: .word 0x4000
valor: .word 0

.text
main:
    LW $t0, sensor_addr

loop:
    LW $t1, 0($t0)
    SW $t1, valor
    J loop
```

## Explicação do Código

- `LW` realiza leitura de dados da memória  
- `SW` armazena o valor coletado  
- `J loop` mantém o sistema em leitura contínua  

O código realiza a leitura contínua de um sensor em memória e armazena o valor coletado.

O uso de Assembly reduz a quantidade de instruções executadas pelo processador, diminuindo o consumo computacional e aumentando a eficiência energética do sistema embarcado.

---

# Equações Utilizadas

## Potência Elétrica

P = V × I

Onde:

- P = potência  
- V = tensão  
- I = corrente  

## Energia

E = P × t

Onde:

- E = energia  
- P = potência  
- t = tempo  

Essas equações são utilizadas para monitorar e calcular o consumo energético durante o funcionamento do eletroposto.

---

# Estratégias de Otimização

## Loop Unrolling

Técnica que reduz a sobrecarga de loops replicando o corpo do laço múltiplas vezes.

### Benefícios

- Redução de desvios  
- Menor número de instruções  
- Melhor desempenho  

## Redução de Hazards de Pipeline

Otimização para evitar conflitos entre instruções no pipeline.

## Minimização de Cache Misses

Melhor organização dos dados em memória para reduzir acessos lentos.

## Uso Eficiente de Registradores

Reduz acessos à memória principal e melhora a velocidade de execução.

---

# Sustentabilidade e Eficiência Energética

O projeto relaciona arquitetura de computadores com sustentabilidade na mobilidade elétrica.

A utilização de código otimizado em Assembly reduz o número de instruções executadas pelo processador, diminuindo o consumo de energia computacional.

A redução de ciclos de clock e instruções executadas diminui diretamente o consumo energético do processador, tornando os eletropostos mais sustentáveis computacionalmente.

Além disso, a escolha de arquiteturas eficientes como RISC-V permite:

- Menor consumo elétrico  
- Melhor uso de energias renováveis  
- Maior eficiência dos eletropostos  
- Redução de desperdício computacional  
- Maior vida útil do hardware  

Com isso, o sistema se torna mais sustentável e adequado para aplicações embarcadas de baixo consumo.

---

# Tecnologias e Ferramentas Utilizadas

- Linguagem Assembly  
- Arquitetura RISC-V  
- MIPS Assembly  
- Sistemas embarcados  
- Microcontroladores ARM Cortex-M  
- Simuladores de arquitetura  

---

# Simuladores Recomendados

- RARS  
- MARS Simulator  
- QtSPIM  
- NASM  
- EMU8086  

---

# Impactos Esperados

- Redução do consumo energético computacional  
- Melhor desempenho dos eletropostos  
- Menor uso de hardware de alto consumo  
- Maior eficiência em sistemas embarcados  
- Melhor aproveitamento de energia renovável  
- Maior sustentabilidade operacional  

---

# Conclusão

O projeto demonstra como conceitos de arquitetura de computadores e programação em Assembly podem ser aplicados em sistemas embarcados para eletropostos.

A utilização de técnicas de otimização em baixo nível permite reduzir o consumo computacional, melhorar o desempenho e aumentar a eficiência energética do sistema.

Dessa forma, a solução contribui diretamente para sustentabilidade, eficiência energética e melhor aproveitamento de recursos computacionais na mobilidade elétrica.