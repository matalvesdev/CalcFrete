# FreteFlex

## Sistema de Cálculo de Frete

**FreteFlex** é um sistema de cálculo de frete que permite aos usuários calcular o custo de envio de pacotes utilizando diferentes estratégias de cálculo de frete. O sistema oferece duas principais opções de frete: **Standard (Normal)** e **Express (Expresso)**, cada uma delas com sua própria fórmula baseada no peso e na distância do envio.

---

## Regras de Negócio

### Tipos de Frete

- **Frete Standard (Normal):**
  - **Fórmula de cálculo:**  
    `custo = peso * 1.0 + distância * 0.5`
  - Oferece um custo acessível, ideal para entregas que não têm urgência.

- **Frete Express (Expresso):**
  - **Fórmula de cálculo:**  
    `custo = peso * 1.5 + distância * 0.75`
  - Mais caro, mas garante entrega mais rápida e prioritária.

### Parâmetros de Entrada

- **Peso do Pacote (`weight`):** O peso do pacote em quilogramas (kg).
- **Distância de Envio (`distance`):** A distância total em quilômetros (km).
- **Tipo de Frete (`type`):** O tipo de frete desejado, podendo ser `"standard"` ou `"express"`.

### Processo de Cálculo de Frete

1. O usuário fornece o peso, a distância do pacote e o tipo de frete.
2. O sistema seleciona a implementação apropriada do `ShippingCalculator` (Standard ou Express) com base no tipo de frete.
3. O custo é calculado utilizando a fórmula correspondente ao tipo de frete.

---

## Endpoint REST

- **GET** `/shipping/calculate`  
  Endpoint para calcular o custo de frete.

  **Parâmetros de consulta:**
  - `weight`: Peso do pacote.
  - `distance`: Distância de envio.
  - `type`: Tipo de frete (`"standard"` ou `"express"`).

  **Retorno:**
  - `shippingCost`: O custo calculado do frete.

---

## Exemplo de Uso

Um usuário deseja enviar um pacote com as seguintes características:
- Peso: **10 kg**
- Distância: **100 km**
- Tipo de frete: **"express"**

O usuário acessa o endpoint `/shipping/calculate` com os parâmetros `weight=10`, `distance=100` e `type=express`.

**Cálculo:**

- Frete Standard:  
  `custo = 10 * 1.0 + 100 * 0.5 = 10 + 50 = 60`

- Frete Express:  
  `custo = 10 * 1.5 + 100 * 0.75 = 15 + 75 = 90`

---

## Licença

Este projeto está sob a licença MIT.

---
