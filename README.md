# Documento de Diseño: F1 Duel (Adaptación de Mokepon)

**Concepto General:**
Adaptar la arquitectura técnica del proyecto *Mokepon* (selección de personaje, movimiento en mapa 2D tipo Canvas y sistema de combate por turnos/decisiones) a una temática de Fórmula 1 enfocada en la estrategia de puesta a punto (*setup*).

## Flujo de Juego (Game Loop)

1. **Selección de Piloto:** El jugador elige su piloto (equivalente a la selección inicial de Mokepon).
2. **Exploración del Paddock:** Los jugadores navegan por el mapa 2D. Al colisionar o cruzarse con un rival, se inicia el duelo.
3. **Fase de Pits (Toma de Decisiones):** En lugar de seleccionar ataques elementales, los jugadores eligen entre **5 configuraciones aerodinámicas** organizadas en un espectro:

* **Opción 1:** Carga mínima / Velocidad punta máxima (ideal para rectas largas).
* **Opción 2:** Balance orientado a velocidad punta.
* **Opción 3:** Setup balanceado (punto medio).
* **Opción 4:** Balance orientado a paso por curva.
* **Opción 5:** Carga aerodinámica máxima (ideal para circuitos técnicos y revirados).

---

### Mecánica de Resolución y Condición de Victoria

* **Parámetro del Circuito:** Cada carrera se disputa en un circuito específico con un *setup óptimo* predefinido (ej. Monza favorece velocidad punta; Mónaco favorece carga aerodinámica).
* **Cálculo del Ganador:** Vence el piloto cuya configuración esté numéricamente más cerca del setup ideal del circuito.
* **Margen de Victoria (*Gap*):** La diferencia de tiempo o distancia al cruzar la meta dependerá de la brecha entre las elecciones:
* Si ambos eligen la misma distancia al óptimo: Empate técnico o definición por un factor secundario (ej. atributos base del piloto).
* A mayor disparidad entre el acierto del ganador y el error del rival, mayor será la brecha de tiempo final (*gap* abismal vs. final cerrado).

---

### Sugerencia para la Elección de Circuito

* **Selección Aleatoria con Aviso Previo (Recomendado):** El circuito se genera al azar al iniciar el duelo y se muestra a ambos jugadores en pantalla antes de entrar a boxes. Esto emula la realidad de la F1 (adaptarse a la pista asignada) y evita empates sistemáticos donde ambos eligen siempre la pista que mejor dominan.
