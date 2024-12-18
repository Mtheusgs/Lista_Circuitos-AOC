# ULA (Unidade Lógica e Aritmética)

## 🔍 Descrição

A ULA (Unidade Lógica e Aritmética) é um componente fundamental em processadores, responsável por realizar operações lógicas (e.g., AND, OR, XOR) e aritméticas (e.g., soma, subtração). Este projeto implementa uma ULA com suporte a múltiplas operações, controladas por sinais de entrada específicos.

O objetivo é projetar um circuito que seja capaz de executar operações básicas em dois operandos (\( A \) e \( B \)) e produzir o resultado adequado, com suporte a sinalizações como carry-out, overflow e zero.

---

## 🖥️ Componentes

Os principais componentes utilizados no circuito incluem:
- **Portas Lógicas**: AND, OR, XOR, NOT.
- **Somador/Subtrator**: Circuito para operações de soma e subtração.
- **Multiplexadores**: Para selecionar a operação com base no sinal de controle.
- **Flip-Flops**: Caso seja necessário armazenar resultados (opcional).
- **Entradas**:
  -  Operandos de 8 bits.
  - \Seletor/Decoder/: Para selecionar a operação.
- **Saídas**:
  - pino de saida 8 bits: Resultado da operação.
  - \( Cout \): Carry-out (transporte).

---

## ⚙️ Implementação

### 1. **Descrição do Circuito**

### **Passo a Passo do Funcionamento**

1. **Cálculo das Operações**:
   - Os blocos de lógica e aritmética calculam os resultados para todas as operações ao mesmo tempo:
     - AND, OR, NOT, XOR, NAND, NOR.
     - Operações aritméticas (\( A + B \), \( A - B \)).
     - Operações de deslocamento (\( A << 2 \), \( A >> 2 \)).

2. **Seleção da Operação**:
   - O código de controle feito pelo, que escolhe qual dos resultados será direcionado para a saída .


3. **Entrega do Resultado**:
   - Após a seleção, a saída \( R[7:0] \) é enviada para os próximos estágios do sistema, como memória ou registros.

   
### 2. **Imagem do Circuito**

  ![Screenshot 2024-12-09 194927](https://github.com/user-attachments/assets/9112e60f-0b5b-46b4-bd5f-e690eaca33e0)

  Operações com apenas portas, foi ultilizada elas mesmos e adcionado um multiplecador pra aplicar o choice no qual é ativo quando escolhemos tal operação.

  -Seletor/decoder 

  ![Screenshot 2024-12-09 195002](https://github.com/user-attachments/assets/372c1cf6-fe4b-42a2-b6cb-27f01911f051) 

  Ultilizado para selecionar a operação que vai ser realizada.

  Operações restantes (soma, subtrator, e shift) 

   - Somador
        Temos mais informações do seu funcionamento em [Arquivo do Logisim Evolution](../docs/somador-8-bits.md) 
   
   ![Screenshot 2024-12-09 201041](https://github.com/user-attachments/assets/5387cbb0-df01-4989-9930-83417d7fea83) 

   - Shift E e Shift D (respectivamente)

  ![Screenshot 2024-12-09 201510](https://github.com/user-attachments/assets/d7319639-e068-499d-9402-8cb654782cc7)

  ![Screenshot 2024-12-09 201554](https://github.com/user-attachments/assets/ebfc4df9-1f49-470e-bb8c-4e6053de779e)

  Para realização de shift de dois a esquerda ou a direita ultizamos no componente final um shift da imagem ligada a cima em outro shift.

  - Subtrator
      ![Screenshot 2024-12-09 201906](https://github.com/user-attachments/assets/88bb884a-45e2-48b3-982a-4a66f0be1775)

  Subtrator ultiliza a soma pelo complemento de dois, ou seja, fazemos da seguite forma, trsnformamos o input no inverso, somamos com um e posteriormente com o outro input, como podemos ver na imagem.
    
  

   

---

## 🔬 Testes

https://github.com/user-attachments/assets/33aef2d9-4158-4b6c-bc40-ad9dda57bda5

### 1. **Método de Teste**

   - Para cada operação, foram testadas combinações diferentes de \( A \) e \( B \).
   - O circuito foi simulado no Logisim Evolution e os resultados foram comparados com valores esperados.

### 2. **Resultados dos Testes**


## Tabela de Operações e Testes

A tabela a seguir apresenta os testes realizados para uma ULA de 8 bits, com as operações na seguinte ordem:
1. AND (\( A \& B \))
2. OR (\( A | B \))
3. NOT (\( \sim A \))
4. NOT (\( \sim B \))
5. NAND (\( \sim(A \& B) \))
6. XOR (\( A \oplus B \))
7. Shift Left (\( A << 1 \))
8. Shift Right (\( A >> 1 \))
9. Soma (\( A + B \))
10. Subtração (\( A - B \))


| \( Op[3:0] \) | Operação              | Entrada (\( A \), \( B \))      | Saída (\( R[7:0] \)) | \( Cout \) | \( Z \) | \( OVF \) |
|---------------|-----------------------|---------------------------------|----------------------|------------|----------|-----------|
| 0000          | AND (\( A \& B \))   | 11001100, 10101010             | 10001000            | -          | 0        | -         |
| 0001          | OR (\( A | B \))     | 11001100, 10101010             | 11101110            | -          | 0        | -         |
| 0010          | NOT (\( \sim A \))   | 11001100, --------             | 00110011            | -          | 0        | -         |
| 0011          | NOT (\( \sim B \))   | --------, 10101010             | 01010101            | -          | 0        | -         |
| 0100          | NAND (\( \sim(A \& B) \)) | 11001100, 10101010         | 01110111            | -          | 0        | -         |
| 0101          | XOR (\( A \oplus B \)) | 11001100, 10101010           | 01100110            | -          | 0        | -         |
| 0110          | Shift Left (\( A << 1 \)) | 11001100, --------         | 10011000            | -          | 0        | -         |
| 0111          | Shift Right (\( A >> 1 \)) | 11001100, --------        | 01100110            | -          | 0        | -         |
| 1000          | Soma (\( A + B \))   | 11001100, 10101010             | 01110110            | 1          | 0        | 0         |
| 1001          | Subtração (\( A - B \)) | 11001100, 10101010          | 00000010            | 0          | 0        | 0         |

---

## Explicação da Tabela

- **Entradas (\( A, B \))**:
  - \( A = 11001100 \) (204 decimal)
  - \( B = 10101010 \) (170 decimal)
- **Operações**:
  - Operações lógicas (\( AND, OR, NOT, NAND, XOR \)) manipulam os bits diretamente.
  - Operações de deslocamento (\( << \), \( >> \)) ajustam os bits do operando \( A \).
  - Operações aritméticas (\( +, - \)) respeitam transporte (\( Cout \)) e estouro (\( OVF \)).
- **Saídas**:
  - \( R[7:0] \): Resultado da operação.
  - \( Cout \): Carry-out para soma/subtração.
  - \( Z \): Indicador de zero (1 se \( R = 0 \)).
  - \( OVF \): Indicador de overflow (para soma/subtração com sinal).


## 📈 Análise

### Resultados Obtidos

- A ULA funcionou corretamente para todas as operações descritas.

### Observações

1. **Complexidade**:
   - O circuito pode ser otimizado com o uso de multiplexadores mais eficientes para selecionar operações.

---

## 📂 Arquivos Relacionados

- [Arquivo do Logisim Evolution](../src/ULA.circ)
