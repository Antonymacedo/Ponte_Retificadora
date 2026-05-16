# Ponte Retificadora ⚡

Circuito eletrônico que converte **corrente alternada (CA) em corrente contínua (CC)** usando quatro diodos dispostos em configuração de ponte. Diferente do retificador de meia onda (que usa apenas um diodo e aproveita só metade do ciclo), a ponte de Graetz aproveita **os dois semiciclos** da onda senoidal — positivo e negativo — resultando em uma saída mais eficiente, com o dobro da frequência de ondulação e muito mais fácil de filtrar.

Na prática, é um dos blocos mais fundamentais de qualquer fonte de alimentação: a tensão da rede elétrica (AC) entra na ponte, sai como corrente contínua (DC) pulsante, passa por um capacitor de filtro e fica estável o suficiente para alimentar circuitos eletrônicos.

---

## Como funciona ⚙️

<img width="582" height="367" alt="image" src="https://github.com/user-attachments/assets/f7b16b49-2d59-4b0f-960e-7f1183ae9bbd" />

O gráfico acima mostra os três sinais principais do circuito:

* **Azul — Entrada AC:** tensão senoidal da rede, alternando continuamente entre valores positivos e negativos.
* **Vermelho — Saída da Ponte:** os quatro diodos trabalham aos pares. No semiciclo positivo, dois deles conduzem; no negativo, os outros dois conduzem invertendo o caminho da corrente — o resultado é uma tensão **sempre positiva**, mas ainda pulsante.
* **Verde — Saída com Capacitor:** o capacitor carrega durante os picos da onda e descarrega lentamente nos vales, suavizando a ondulação. O resultado é uma tensão DC muito mais estável, próxima de uma linha reta.

> 💡 Quanto maior o capacitor (µF) e menor a corrente consumida pela carga, mais lisa fica essa linha verde — e mais próxima de uma fonte DC ideal.

### Por dentro da ponte — o caminho da corrente

```
Semiciclo positivo:   AC+ → D1 → Carga → D3 → AC-
Semiciclo negativo:   AC- → D2 → Carga → D4 → AC+
```

Em ambos os casos, a corrente passa pela carga sempre no **mesmo sentido** — isso é a retificação de onda completa.

---

## Cálculos úteis 🧮

Antes de montar, vale entender o que esperar da saída:

| Grandeza | Fórmula | Exemplo (12V AC) |
|---------|---------|-----------------|
| Tensão de pico | Vpico = Vrms × √2 | 12 × 1,414 = **~17V** |
| Queda nos diodos | ≈ 1,4V (2 diodos em série) | — |
| Tensão DC final | Vdc ≈ Vpico − 1,4V | 17 − 1,4 = **~15,6V** |
| Ondulação (ripple) | Vr = Idc / (2 × f × C) | depende da carga |

> Esses valores são aproximados. A tensão real cai conforme a carga aumenta.

---

## Lista de materiais 🛒

<img width="394" height="318" alt="image" src="https://github.com/user-attachments/assets/716d2cec-64c4-47e5-be13-515f38d83e85" />

| # | Componente | Qtd | Observação |
|---|-----------|-----|-----------|
| 1 | Diodo M4007 | 4x | Suporta 1A / 1000V |
| 2 | Born banana | 4x | Entradas AC e saídas DC+/DC− |
| 3 | Capacitor eletrolítico 1000µF 25V | 1x | Filtro de ondulação |
| 4 | Placa fenolite / protoboard | 1x | Para montagem do circuito |
| 5 | Fios de cobre | — | Para as trilhas e conexões |

> ⚠️ Também são necessários ferramentas como chave philips, ferro de solda e estanho para montagem em placa.

### Sobre os componentes

**Diodo M4007** — parte da família 1N400x, suporta até 1A de corrente média e 1000V de tensão reversa. Para cargas que consomem mais de 1A, substitua por **1N5408** (3A) ou use uma ponte já encapsulada como a **KBPC2510** (25A).

**Capacitor 1000µF 25V** — responsável por filtrar a ondulação da saída. A tensão de trabalho (25V) deve ser sempre maior que a tensão de pico esperada na saída. Se for usar em uma fonte de 12V AC por exemplo, a tensão de pico chega a ~17V — o capacitor de 25V está adequado, mas um de 35V daria mais margem de segurança.

---

## Circuito 🔌

<img width="424" height="473" alt="image" src="https://github.com/user-attachments/assets/cd0a46a0-c387-4e7d-ab67-01b89adf9736" />

O diagrama mostra a configuração clássica em ponte: as entradas AC nos dois nós laterais, a saída DC+ no nó superior e o GND (DC−) no nó inferior.

> ⚠️ **Atenção:** nunca conecte este circuito diretamente à rede elétrica de 127V ou 220V sem antes passar por um **transformador** que reduza a tensão para um nível seguro. O circuito em si não possui proteção contra sobretensão.

---

## Montagem na placa 🔧

A montagem foi feita em placa fenolite com trilhas de cobre. Os quatro diodos foram posicionados em configuração de losango (a forma clássica da ponte), com o capacitor conectado na saída DC.

**Vista superior**

<img width="384" height="512" alt="image" src="https://github.com/user-attachments/assets/a281852b-d816-4507-9ff4-ea4144ac1bf0" />

---

**Vista inferior** — trilhas de solda

<img width="384" height="512" alt="image" src="https://github.com/user-attachments/assets/d4d8a5fa-5bf7-44b9-88da-bab4d4ad2477" />

> OBS: o capacitor não aparece nas fotos — foi adicionado após o registro.

---

## Resultados ❗

Vídeo do circuito em funcionamento:

https://github.com/user-attachments/assets/fdcfdbf0-0c8a-4c5a-9844-8bef499734a4

---

**Forma de onda sem retificar — AC puro**

<img width="50%" alt="Forma de onda sem retificar" src="https://github.com/user-attachments/assets/d895d2e6-40ac-4ae7-a1ac-bc237670ee15" />

Sinal senoidal clássico: oscila entre positivo e negativo simetricamente.

---

**Forma de onda retificada — saída da ponte**

<img width="50%" alt="Forma de onda retificada" src="https://github.com/user-attachments/assets/71436ee0-48e1-4e68-89dd-23112ec1fc70" />

Os semiciclos negativos foram "espelhados" para cima — a tensão agora é sempre positiva, mas ainda pulsa no dobro da frequência original (120Hz para uma rede de 60Hz).

---

**Retificador montado no suporte, conectado nos borns**

<img width="66%" alt="Retificador no suporte" src="https://github.com/user-attachments/assets/c9791672-4344-4ac6-8da5-9dad5402cd3f" />

---

## Possíveis problemas e soluções 🛠️

| Sintoma | Causa provável | Solução |
|--------|---------------|---------|
| Saída DC com metade da tensão esperada | Um diodo queimado ou invertido | Teste cada diodo com multímetro no modo diodo |
| Muita ondulação na saída | Capacitor pequeno ou ausente | Aumente a capacitância (ex: 2200µF ou 4700µF) |
| Capacitor esquentando ou estourando | Polaridade invertida ou tensão acima do limite | Revise a polaridade e use capacitor de tensão maior |
| Tensão DC menor que o esperado | Queda nos diodos + resistência interna | Normal — reveja os cálculos com a fórmula acima |
| Circuito funciona mas saída oscila muito sob carga | Capacitor insuficiente para a corrente da carga | Adicione mais capacitância em paralelo |

---

## Considerações 💡

- Sempre observe a **polaridade dos diodos** ao montar — inverter um deles quebra o funcionamento da ponte.
- O capacitor eletrolítico tem polaridade: ligue o terminal **negativo no GND** e o positivo na saída DC+.
- A tensão de trabalho do capacitor deve ser **pelo menos 20% maior** que a tensão de pico esperada na saída.
- Para testar o circuito com segurança, use um **transformador de baixa tensão** (6V, 9V ou 12V AC) em vez da rede diretamente.
- Este circuito é a base de praticamente toda fonte linear — pode ser complementado com um regulador de tensão como o **LM7805** (5V) ou **LM7812** (12V) para uma saída ainda mais estável.

---

### Referências 📚

- [All About Circuits — Full-Wave Rectifier](https://www.allaboutcircuits.com/textbook/semiconductors/chpt-3/full-wave-rectifiers/)
- [Datasheet Diodo M4007](https://www.vishay.com/docs/88503/m4007.pdf)
- [Eletrogate — Tutoriais de Eletrônica](https://blog.eletrogate.com/)
