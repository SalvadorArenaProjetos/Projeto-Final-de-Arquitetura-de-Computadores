# Processador RISC-V em Logisim Evolution

Este projeto implementa um processador simples baseado na arquitetura RISC-V RV32I no Logisim Evolution. O objetivo é demonstrar o funcionamento interno de um processador, incluindo datapath, unidade de controle, banco de registradores, memória e o ciclo completo de busca, decodificação e execução.

---

## Integrantes do Projeto
| Nome                             |     RA    |
|----------------------------------|-----------|
| Aline Cristina Ribeiro de Barros | 081230021 |
| Luis Gustavo de Oliveira Carneiro| 081230029 |
| João Victor Pereira Andrade      | 081230010 |
| André Mendes Garcia              | 081230012 |
| Roger Rocha da Silva             | 081230045 |

---

## Arquitetura Implementada

O processador segue um modelo de ciclo único e conta com os seguintes módulos:

- ULA de 32 bits  
- Banco de Registradores (32 registradores x 32 bits)  
- Unidade de Controle  
- Extensor de Imediatos  
- Memória ROM (instruções)  
- Memória RAM (dados)  
- PC (Program Counter)  
- Barramentos de controle e dados

### Datapath (Representação ASCII)

            +-------------------+
            |        PC         |
            +---------+---------+
                      |
                      v
              +---------------+
              |     ROM       |
              +---+-------+---+
                  |       |
                  |       +------------------------------------+
                  v                                            |
        +-------------------------+                             |
        |     Unidade de Controle |                             |
        +-----------+-------------+                             |
                    |                                           |
            +-------+-------+                                   |
            |  Extensor de  |                                   |
            |   Imediato    |                                   |
            +-------+-------+                                   |
                    |                                           |
                    v                                           |
   +----------------------------------+        +----------------+-------+
   |       Banco de Registradores     |<------>|        ULA            |
   +----------------------------------+        +------------------------+
                    |                                           |
                    +-------------------------------------------+


## Subcircuitos

| Subcircuito | Descrição |
|-------------|------------|
| ULA | Operações aritméticas e lógicas |
| Banco de Registradores | Armazena x0–x31 |
| Unidade de Controle | Gera sinais a partir do opcode |
| Extensor de Imediatos | Gera valores para instruções I, S, B, U e J |
| ROM | Armazena instruções |
| RAM | Armazena dados |
| PC | Contador de programa |

---

## Instruções Implementadas

| Instrução | Tipo | Função         |
|----------|------|-----------------|
| ADD      | R | Soma               |
| SUB      | R | Subtração          |
| AND      | R | E lógico           |
| OR       | R | OU lógico          |
| XOR      | R | XOR                |
| ADDI     | I | Soma imediata      |
| LW       | I | Load word          |
| SW       | S | Store word         |
| BEQ      | B | Desvio se igual    |
| BNE      | B | Desvio se diferente|
| JAL      | J | Salto absoluto     |
| JALR     | I | Salto relativo     |

---

## Ciclo de Instrução

### Fluxo

+-------------+ +------------------+ +------------------+
| Busca | ---> | Decodificação | ---> | Execução |
+-------------+ +------------------+ +------------------+
^ | |
| v v
+----------- Atualização do PC <--------------+


### Etapas

1. **Busca (IF):** A ROM retorna a instrução no endereço do PC.  
2. **Decodificação (ID):** Unidade de controle define sinais e lê registradores.  
3. **Execução (EX):** ULA executa operação ou calcula endereço.  
4. **Memória (MEM):** LW ou SW acessam RAM.  
5. **Write Back (WB):** Resultado retorna ao registrador destino.

---


---

## Instruções de Execução

1. Abra o Logisim Evolution.  
2. Carregue o arquivo.  
3. Verifique os subcircuitos conectados.  
4. Carregue um programa na ROM.  
5. Execute a simulação passo a passo usando o clock.  
6. Observe PC, registradores, ULA e RAM para verificar o funcionamento correto.

---

## Vídeo de Referência

Link:
