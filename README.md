# mecanismos
Calculadora de mecanismos: Síntesis Algebraica

- Análisis de Posición
1. Motor Matemático: Contiene las ecuaciones paramétricas para evitar bucles. Usa las sustituciones de K_1 a K_5, las reglas del discriminante para identificar los puntos ciegos (límites de Grashof) y la tangente del medio ángulo para calcular con precisión theta_3 y theta_4.

2. Manejo de Ramas: Se incorporó el signo exacto que menciona la diapositiva: "Abierta: signo -", "Cruzada: signo +".

3. Renderizado en un Plano Cartesiano Correcto: Los <canvas> en la web tienen por defecto el eje Y invertido (hacia abajo). He usado la matriz de transformación de Canvas (ctx.scale(scale, -scale)) para que matemáticamente se comporte como el plano X-Y que conocemos en física.

4. Autoescalado Dinámico: No importa si la suma de los eslabones da 30, o 300; el Canvas calcula el espacio necesario (maxReach = Math.max(a + b, d + c, a + c, d + b)) para mantener el mecanismo perfectamente centrado a la vista.

5. Detección de Grashof: Verifica en tiempo real la sumatoria del eslabón más corto y más largo vs los demás, avisando interactivamente al usuario si está frente a un mecanismo que gire totalmente (manivela-balancín) o si limitará su movimiento (no-grashof), explicando visualmente si no ensambla porque los círculos de la manivela y el balancín dejan de intersectarse.


- Simulador Universal
El simulador ha sido expandido para abarcar nuevas topologías cinemáticas, convirtiéndose en una herramienta de análisis de posición universal. Las actualizaciones incluyen la implementación matemática y visual de los mecanismos de Manivela-Corredera y Corredera-Manivela, basados en el método analítico de lazo vectorial.

CARACTERÍSTICAS AGREGADAS: 
- Selector Multimodo: Se agregó un menú desplegable en el panel de control que permite al usuario alternar dinámicamente entre tres tipos de mecanismos:

1. Cuatro Barras (Rotación a Rotación).

2. Manivela-Corredera (Rotación a Traslación).

3. Corredera-Manivela (Traslación a Rotación).

- Interfaz Dinámica e Interactiva: Las etiquetas y los campos de entrada se adaptan automáticamente según el modo seleccionado.

* En los modos con corredera, el parámetro c pasa a representar el descentrado (offset) y el parámetro d representa la posición de la corredera.

* El campo de entrada cambia lógicamente: en el modo Manivela-Corredera se bloquea d (es el resultado) y se ingresa el ángulo θ_2; en el modo Corredera-Manivela se bloquea θ_2 (es el resultado visual y numérico) y se ingresa la posición d.

- Motor de Cálculo Analítico Mejorado:

* Manivela-Corredera: Implementación de las funciones de arcoseno para calcular el ángulo del acoplador θ_3 y la posición de la corredera d para los circuitos abierto y cruzado.

* Corredera-Manivela: Resolución de la ecuación cuadrática (discriminante) y uso del método de la tangente de medio ángulo (con atan2) para calcular con exactitud los ángulos de la manivela θ_2 y el acoplador θ_3 en sus dos ramas (Rama 1 y Rama 2).

* Validación de Ensamblaje: Se integraron validaciones matemáticas para evitar errores NaN. Si el valor absoluto en el arcoseno es mayor a 1, o si el discriminante es negativo, la UI alerta claramente al usuario con una equeta de "No ensambla".

- Actualización del Renderizado:

* Se añadió la lógica de dibujo para representar visualmente el eje de deslizamiento, el descentrado y el bloque de la corredera.

* El autoescalado del canvas fue ajustado para considerar el máximo alcance dinámico de la corredera dependiiendo si el mecanismo es válido o si se encuentra en un punto donde no se arma. 

