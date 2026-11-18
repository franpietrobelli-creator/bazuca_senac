# Bazuca: painel de controle

Painel web para controlar uma **bazuca artesanal movida a servomotores e um ESP32-S3**. Este repositório tem o **simulador do painel** (`bazuca_controles.html`), feito em HTML, CSS e JavaScript puro, sem bibliotecas.

## Controles

| Controle | Como funciona | Faixa |
|---|---|---|
| **Elevação** | Barra vertical com um marcador que você arrasta para cima ou para baixo. Topo = +45°, meio = 0°, base = -45° | -45° a +45° |
| **Direção** | Botão circular que gira com o mouse, como um volante (0° em cima, aumentando no sentido horário) | 0° a 359° |
| **Atirar** | Simula o disparo e mostra a mensagem "💥 Disparo realizado!" com o ângulo vertical e a direção do momento | — |

Os valores atuais aparecem na tela em tempo real ("Ângulo vertical" e "Direção horizontal").

## Como o código funciona

- `anguloVertical` e `direcaoHorizontal` guardam os valores atuais dos controles
- `moverMarcador()` converte a posição do marcador na barra (em pixels) para um ângulo de -45° a +45°, sem deixar o marcador sair da barra
- `centralizarMarcador()` começa a barra no meio (0°)
- `calcularAngulo()` calcula o ângulo do mouse em relação ao centro do botão circular, e `girarPara()` gira o botão até esse ângulo
- Os eventos `pointerdown`, `pointermove` e `pointerup` controlam o arraste, o que funciona com mouse e com toque

Na bazuca de verdade, esses valores viram os ângulos dos servomotores (elevação e direção) controlados pelo ESP32-S3.

## Como usar

Abra o `bazuca_controles.html` no navegador.
