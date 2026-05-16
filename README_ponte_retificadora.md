# Ponte Retificadora ⚡

Circuito eletrônico que converte **corrente alternada (CA) em corrente contínua (CC)** usando quatro diodos em configuração de ponte. Tanto o semiciclo positivo quanto o negativo da onda senoidal são aproveitados, resultando em uma saída sempre no mesmo sentido — que pode ser suavizada com um capacitor.

Na prática, é um dos blocos mais fundamentais de fontes de alimentação: a rede elétrica (AC) passa pela ponte, vira corrente contínua (DC) e pode ser regulada para alimentar circuitos eletrônicos.

---

## Como funciona ⚙️

<img width="582" height="367" alt="image" src="https://github.com/user-attachments/assets/f7b16b49-2d59-4b0f-960e-7f1183ae9bbd" />

O gráfico acima mostra três sinais:

* **Azul (Entrada AC):** tensão senoidal da rede — alterna entre positivo e negativo.
* **Vermelho (Saída da Ponte):** os diodos invertem os semiciclos negativos, deixando a saída sempre positiva, mas ainda com ondulação.
* **Verde (Saída com Capacitor):** o capacitor carrega nos picos e descarrega lentamente, "nivelando" a tensão — o resultado é uma DC quase contínua.

> 💡 Quanto maior o capacitor (µF) e menor a carga consumindo corrente, mais lisa fica a linha verde.

---

## Lista de materiais 🛒

<img width="394" height="318" alt="image" src="https://github.com/user-attachments/assets/716d2cec-64c4-47e5-be13-515f38d83e85" />

| # | Componente | Qtd |
|---|-----------|-----|
| 1 | Diodo M4007 | 4x |
| 2 | Born banana | 4x |
| 3 | Capacitor 1000µF 25V | 1x |

> ⚠️ Também são necessários fios de cobre e ferramentas como chave philips.

---

## Circuito 🔌

<img width="424" height="473" alt="image" src="https://github.com/user-attachments/assets/cd0a46a0-c387-4e7d-ab67-01b89adf9736" />

> ⚠️ **Atenção:** não utilize este circuito diretamente em 127V ou 220V como mostrado no diagrama. Use um transformador para reduzir a tensão antes da ponte.

---

## Montagem na placa 🔧

**Vista superior**

<img width="384" height="512" alt="image" src="https://github.com/user-attachments/assets/a281852b-d816-4507-9ff4-ea4144ac1bf0" />

---

**Vista inferior**

<img width="384" height="512" alt="image" src="https://github.com/user-attachments/assets/d4d8a5fa-5bf7-44b9-88da-bab4d4ad2477" />

> OBS: o capacitor não aparece nas fotos acima.

---

## Resultados ❗

https://github.com/user-attachments/assets/fdcfdbf0-0c8a-4c5a-9844-8bef499734a4

---

**Forma de onda sem retificar**

<img width="50%" alt="Forma de onda sem retificar" src="https://github.com/user-attachments/assets/d895d2e6-40ac-4ae7-a1ac-bc237670ee15" />

---

**Forma de onda retificada**

<img width="50%" alt="Forma de onda retificada" src="https://github.com/user-attachments/assets/71436ee0-48e1-4e68-89dd-23112ec1fc70" />

---

**Retificador montado no suporte, conectado nos borns**

<img width="66%" alt="Retificador no suporte" src="https://github.com/user-attachments/assets/c9791672-4344-4ac6-8da5-9dad5402cd3f" />

---

## Considerações 💡

- Sempre observe a **polaridade dos diodos** ao montar — inverter um deles quebra o funcionamento da ponte.
- O capacitor também tem polaridade: ligue o **negativo no GND** e o positivo na saída DC.
- Para cargas maiores, use diodos com corrente nominal mais alta (ex: M4007 suporta até 1A — para mais, use 1N5408 ou ponte já encapsulada como a KBPC).
- A tensão de saída DC será aproximadamente **1,4× a tensão RMS de entrada**, menos a queda dos dois diodos em condução (~1,4V total).
