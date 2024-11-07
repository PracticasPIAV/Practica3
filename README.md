# Práctica 3: Procesamiento de Imágenes

**Autores**: Alejandro Bolaños García y David García Díaz

## Introducción
Esta práctica aborda varias técnicas de procesamiento de imágenes, como ecualización de histogramas, filtros de suavizado y transformaciones, empleando Python y OpenCV. Cada ejercicio demuestra distintos efectos visuales aplicados a imágenes y video, incluyendo la manipulación de contrastes, bordes, y mezclas de imágenes.

## Objetivos
- Aplicar transformaciones de imágenes para obtener efectos visuales variados.
- Utilizar técnicas avanzadas de procesamiento como la ecualización de histograma y filtrado.
- Generar videos que muestren transiciones de efectos visuales.

## Desarrollo

### Ejercicio 1: Inversión y revelado progresivo
Este ejercicio utiliza una transformación simple de inversión de colores y la creación de un video que revela progresivamente la imagen original.  
Para invertir la imagen, se utiliza la operación \( 255 - \text{imagen}(i, j) \), lo que convierte cada píxel a su color opuesto en el espectro de color RGB. Luego, se utiliza un bucle para reemplazar progresivamente cada columna en la imagen invertida con la correspondiente columna de la imagen original.

**Funciones clave:**
- `cv.VideoWriter()`: establece un objeto de video que requiere la tasa de fotogramas (fps), dimensiones y el codec. Aquí, se usa el codec `mp4v` para generar un video en formato MP4.
- `frame[:, i] = imagen[:, i]`: esta instrucción reemplaza cada columna de la imagen invertida por la original en cada iteración, creando un efecto de "revelado" en el video.

### Ejercicio 2: Ecualización de histograma y filtrado bilateral
Este ejercicio aplica ecualización de histograma a una imagen en escala de grises, mejorando el contraste, seguido de un filtro bilateral para reducir el ruido manteniendo los bordes.  

**Funciones clave:**
- `cv.calcHist()`: calcula el histograma de la imagen, mostrando la distribución de niveles de gris. Esto permite analizar el impacto de la ecualización.
- `cv.bilateralFilter()`: requiere el diámetro del filtro y las desviaciones sigma para color y espacio, que controlan el alcance del suavizado y la preservación de bordes.

### Ejercicio 3: Filtrado mediano acumulativo
Este ejercicio aplica un filtro mediano de manera acumulativa a una imagen y guarda el proceso en un video. En un bucle de 100 iteraciones, aplica repetidamente el filtro mediano a la imagen, suavizándola progresivamente en cada paso.

**Funciones clave:**
- `cv.medianBlur()`: filtra cada píxel con la mediana de los píxeles cubiertos por el kernel, reduciendo ciertos tipos de ruido (como el ruido de sal y pimienta) y manteniendo los bordes definidos.

### Ejercicio 4: Detección de bordes y suavizado gaussiano
En este ejercicio, se utiliza el operador de Sobel para detectar bordes en una imagen en escala de grises, seguido de un filtro gaussiano para suavizar la imagen.

**Funciones clave:**
- `cv.Sobel()`: calcula la derivada de la imagen en las direcciones X o Y, destacando bordes.
- `cv.GaussianBlur()`: suaviza la imagen aplicando un filtro gaussiano, controlado por el tamaño de kernel y sigma.

### Ejercicio 5: Eliminación de ruido en imagen mediante filtro mediano
Este ejercicio se centra en la eliminación de ruido en la imagen `imagen6.png` aplicando un filtro mediano con un kernel de 3x3. Este filtro es efectivo para eliminar ruido puntual mientras preserva bordes definidos.

**Funciones clave:**
- `cv.medianBlur()`: aplica el filtro mediano sobre la imagen, utilizando una ventana de tamaño 3x3 y repitiendo la operación cinco veces para maximizar la eliminación de ruido sin perder detalles.

### Ejercicio 6: Mezcla cíclica de imágenes
Este ejercicio genera un video que alterna entre dos imágenes mediante una combinación cíclica basada en la función coseno.

**Funciones clave:**
- `math.cos()`: calcula el peso de cada imagen en la mezcla, creando una transición suave y cíclica.
- Operaciones en Numpy: permite una mezcla suave con valores decimales, evitando la pérdida de precisión.

## Conclusión
La práctica permitió explorar el potencial de OpenCV y Numpy en el procesamiento de imágenes y video. Se logró manipular y combinar imágenes utilizando distintos filtros y transformaciones, entendiendo el funcionamiento técnico de funciones clave como `cv.VideoWriter()`, `cv.Sobel()` y `cv.equalizeHist()`. Estas técnicas son útiles para futuros proyectos en procesamiento de imágenes.
