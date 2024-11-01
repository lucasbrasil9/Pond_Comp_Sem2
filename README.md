# Ponderada Semana 3 de Computação | Semáforo 
Estudante: Lucas Paiva Brasil | T11 | G04

## Relatório do Projeto de Semáforo com Arduino Uno

Este projeto simula o funcionamento de um semáforo usando o microcontrolador **Arduino Uno** e LEDs para representar as luzes **vermelha**, **amarela** e **verde**. O código controla as fases do semáforo, alternando os LEDs com os tempos especificados. Para complementar o código foi utlizado a lógica de ponteiros para deixar o código mais flexível.

### Componentes e Especificações

| Componente     | Quantidade | Especificações                          |
|----------------|------------|-----------------------------------------|
| Arduino Uno    | 1          | Microcontrolador, 5V, 14 pinos digitais |
| LED            | 1          | LED cor vermelha                        |
| LED            | 1          | LED cor amarela                         |
| LED            | 1          | LED cor verde                           |
| Resistores     | 3          | 330Ω (limitador de corrente para LEDs)  |
| Protoboard     | 1          | Base para montagem de circuitos         |
| Cabos Jumper   | 6        | Conexão entre resistores, arduino e LEDs - Macho-Fêmea |
| Cabos Jumper   | 4        | Conexão entre resistores e arduino - Macho-Macho |

### Código para o Arduino Uno

Aqui está o código ajustado para o Arduino Uno:

```cpp
const int LED_VERMELHO = 13;
const int LED_AMARELO = 12;
const int LED_VERDE = 11;

const int* pinoVermelho = &LED_VERMELHO;
const int* pinoAmarelo = &LED_AMARELO;
const int* pinoVerde = &LED_VERDE;

void setup() {
  pinMode(*pinoVermelho, OUTPUT);
  pinMode(*pinoAmarelo, OUTPUT);
  pinMode(*pinoVerde, OUTPUT);
}

void loop() {
  // Fase 1: Vermelho - 6 segundos
  digitalWrite(*pinoVermelho, HIGH);
  digitalWrite(*pinoAmarelo, LOW);
  digitalWrite(*pinoVerde, LOW);
  delay(6000);

  // Fase 2: Amarelo - 2 segundos
  digitalWrite(*pinoVermelho, LOW);
  digitalWrite(*pinoAmarelo, HIGH);
  digitalWrite(*pinoVerde, LOW);
  delay(2000);

  // Fase 3: Verde - 2 segundos
  digitalWrite(*pinoVermelho, LOW);
  digitalWrite(*pinoAmarelo, LOW);
  digitalWrite(*pinoVerde, HIGH);
  delay(2000);

  // Fase 4: Verde - 2 segundos (tempo adicional)
  delay(2000);

  // Fase 5: Amarelo - 2 segundos
  digitalWrite(*pinoVermelho, LOW);
  digitalWrite(*pinoAmarelo, HIGH);
  digitalWrite(*pinoVerde, LOW);
  delay(2000);

}
```

### Funcionamento do Código

1. **Definição dos Pinos**: Os LEDs estão conectados aos pinos 13, 12 e 11.
2. **Ponteiros**: Ponteiros `pinoVermelho`, `pinoAmarelo` e `pinoVerde` armazenam os endereços dos pinos, permitindo o controle indireto.
3. **Fases do Semáforo**:
   - **Vermelho**: 6 segundos.
   - **Amarelo**: 2 segundos.
   - **Verde**: 2 segundos, mais 2 segundos de tempo extra para pedestres.
   - **Amarelo**: 2 segundos novamente.
   
### Conclusão

Este projeto é uma ótima introdução ao uso de ponteiros e ao controle de dispositivos externos com o Arduino Uno. A utilização de ponteiros torna o código mais flexível para futuras modificações.
