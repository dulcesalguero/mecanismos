# mecanismos
Calculadora de mecanismos: Síntesis Algebraica

- Análisis de Posición
1. Motor Matemático: Contiene las ecuaciones paramétricas para evitar bucles. Usa las sustituciones de K_1 a K_5, las reglas del discriminante para identificar los puntos ciegos (límites de Grashof) y la tangente del medio ángulo para calcular con precisión theta_3 y theta_4.

2. Manejo de Ramas: Se incorporó el signo exacto que menciona la diapositiva: "Abierta: signo -", "Cruzada: signo +".

3. Renderizado en un Plano Cartesiano Correcto: Los <canvas> en la web tienen por defecto el eje Y invertido (hacia abajo). He usado la matriz de transformación de Canvas (ctx.scale(scale, -scale)) para que matemáticamente se comporte como el plano X-Y que conocemos en física.

4. Autoescalado Dinámico: No importa si la suma de los eslabones da 30, o 300; el Canvas calcula el espacio necesario (maxReach = Math.max(a + b, d + c, a + c, d + b)) para mantener el mecanismo perfectamente centrado a la vista.

5. Detección de Grashof: Verifica en tiempo real la sumatoria del eslabón más corto y más largo vs los demás, avisando interactivamente al usuario si está frente a un mecanismo que gire totalmente (manivela-balancín) o si limitará su movimiento (no-grashof), explicando visualmente si no ensambla porque los círculos de la manivela y el balancín dejan de intersectarse.
