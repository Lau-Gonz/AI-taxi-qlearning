# Solución del Problema del Taxi con Q-learning

## Descripción del Problema del Taxi

El problema del taxi se modela como un entorno discreto en Gym, con estados, acciones y recompensas. Los estados incluyen la ubicación del taxi, la posición del pasajero, la ubicación del destino y la presencia del pasajero en el taxi. Las acciones posibles son movimientos en las cuatro direcciones, recoger y dejar al pasajero. Las recompensas se asignan según la ejecución de acciones, destacando la entrega exitosa del pasajero.

### Recompensas:

- Se otorga una recompensa de -1 por cada paso realizado, a menos que se desencadene otra recompensa.
- Se otorga una recompensa de +20 por entregar exitosamente al pasajero.
- Se penaliza con -10 al ejecutar las acciones de recoger/dejar al pasajero de manera ilegal.

## Algoritmo de Q-learning

Se utiliza el algoritmo de Q-learning para resolver el problema del taxi. Este algoritmo utiliza una tabla Q para almacenar los valores de utilidad de cada par estado-acción. Inicialmente, la tabla se inicia con ceros. La actualización de los valores Q se realiza mediante la ecuación de Bellman:

$$
Q(s, a) = (1 − \alpha) \cdot Q(s, a) + \alpha \cdot \left(R + \gamma \cdot max \; Q(s', a')\right)
$$

Donde:

- $Q(s, a)$ es el valor actualizado para el par estado-acción.
- $\alpha$ es la tasa de aprendizaje.
- $R$ es la recompensa obtenida por la acción $a$ en el estado $s$.
- $\gamma$ es el factor de descuento.
- $max \; Q(s′, a′)$ es el valor máximo de la tabla $Q$ para el próximo estado $s'$.

Se emplea un enfoque ϵ-greedy para equilibrar la exploración y explotación. Con probabilidad ϵ, el agente elige una acción aleatoria; de lo contrario, selecciona la acción con el máximo valor en la tabla Q. Se ajustan hiperparámetros como la tasa de aprendizaje ($\alpha$), el factor de descuento ($\gamma$) y la probabilidad de exploración ($\epsilon$) para optimizar el rendimiento del algoritmo.

## Requerimientos de ejecución

```bash
pip install -r requirements.txt
```