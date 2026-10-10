# GUÍA DEFINITIVA DE CONFIGURACIÓN Y OPERACIÓN
## Consola Behringer Xenyx (1832FX / Series FX y Análogas)

---

## 1. Solución al Problema Actual y Por Qué Ocurría

### A. ¿Solo el botón `MAIN` de la cajita `SOURCE` debe estar presionado?
**Sí, para el uso normal diario únicamente debe estar presionado el botón `MAIN` dentro de la caja `SOURCE`.**
* Los 3 botones (`CD/TAPE`, `SUB 1-2`, `MAIN`) eligen qué señal se envía a los **audífonos** (`PHONES`) y al **vúmetro de luces L/R**.
* Si presionas más de uno, sumarás las señales en los audífonos. Al dejar únicamente presionado **`MAIN`**, los vúmetros y audífonos reflejarán con exactitud lo que está saliendo por la mezcla general.

### B. ¿Por qué los LEDs del Main Mix aún no se mueven si en Windows ya entra la señal?
Hay una diferencia técnica muy importante entre los medidores físicos de la consola y la entrada de audio de Windows:
1. **El rango de los LEDs de la consola:** El primer led verde de abajo de la consola empieza en **-30 dB**. Si tu nivel de voz está entre -45 dB y -32 dB, para la consola la señal es demasiado suave para encender el primer foco, pero **Windows sí la escucha** porque la tarjeta de sonido del PC tiene un amplificador digital integrado con mucha ganancia (sensibilidad alta).
2. **El Shure Beta 58A es un micrófono dinámico:** Produce una señal de voltaje baja en comparación con micrófonos de condensador.
3. **Cómo calibrar la Ganancia (Gain Staging) para que los LEDs se muevan correctamente:**
   * Activa temporalmente el botón **`SOLO`** en el Canal 1 (el led rojo de prueba se encenderá).
   * Habla al micrófono con la fuerza y distancia real con la que vas a cantar o hablar.
   * Ve subiendo lentamente la perilla negra superior de **`GAIN`** (del Canal 1) hasta que las luces alcancen la marca de **0 dB** (los leds verdes superiores o el primer amarillo).
   * **Desactiva el botón `SOLO`** (el led rojo se apagará).
   * Deja el fader deslizante del Canal 1 en **0 dB** y los faders grises de **MAIN MIX en 0 dB**.
   * Ahora, cuando hables fuerte, los vúmetros verdes del Main Mix **reaccionarán y subirán con normalidad** al ritmo de tu voz.

### C. El botón traicionero: `CD/TAPE TO MAIN`
* Este botón (arriba de la perilla blanca de audífonos) toma la entrada RCA y la fuerza dentro del bus maestro.
* Al usar cables hacia la PC, si ese botón está presionado genera un corte/bloqueo de señal o un bucle de retroalimentación (*feedback loop*). **Debe permanecer siempre LEVANTADO/DESACTIVADO para grabar.**

---

## 2. Configuración para Conexión con Windows y Adobe Audition

### Conexión Física:
* **Salida de consola:** 2 cables RCA desde **`CD/TAPE OUTPUT`**.
* **Entrada de PC:** Conector Jack 3.5mm estéreo conectado al **Jack AZUL (Línea de Entrada / Line In)** en la parte trasera de la torre.

### Configuración en Windows:
1. **Permisos de micrófono:**
   * `Configuración` > `Privacidad y seguridad` > `Micrófono`.
   * Habilitar: *Acceso al micrófono* y *Permitir que las aplicaciones de escritorio accedan al micrófono*.
2. **Propiedades de sonido clásicas (`mmsys.cpl`):**
   * Pestaña **Grabar** > Doble clic en **Línea de entrada (Realtek)**.
   * Pestaña **Niveles:** Ajustar entre **75 y 85**. Asegurarse de que el icono del altavoz no tenga la cruz roja de silenciado.
   * Pestaña **Opciones avanzadas:** Formato predeterminado en **2 canales, 24 bits (o 16 bits), 48000 Hz (Calidad de estudio)**.

### Configuración en Adobe Audition:
1. **Hardware de Audio:**
   * Menú `Edición` > `Preferencias` > `Hardware de audio`.
   * **Clase de dispositivo:** `MME` (o `ASIO` si usas ASIO4ALL).
   * **Entrada predeterminada:** `Línea de entrada (Realtek Audio)`.
   * **Salida predeterminada:** Tus altavoces/auriculares habituales de la PC.
   * **Tamaño del búfer / Latencia:** 512 o 256 muestras para evitar retrasos y chasquidos.
2. **Grabación en la Pista (Vista Multipista o Editor de Onda):**
   * El micrófono es una señal **Mono**. 
   * En la pista multipista de Audition, asigna la entrada como: `Mono` > `Línea de entrada L` (o R). Si seleccionas Estéreo, tu voz solo se escuchará por un lado de los audífonos.
   * Activa el botón **[R]** (Armar para grabar) y el botón **[I]** (Monitor) para comprobar el nivel en pantalla.
   * **Nivel objetivo en Audition:** Tu voz debe picar entre **-12 dB y -6 dB** en el vúmetro de Audition. Nunca permitas que llegue a 0 dB (rojo) para evitar distorsión digital (*clipping*).

---

## 3. Configuración para Enviar Señal a 2 Parlantes en Vivo (PA / Activos)

### Conexión Física:
* **Salidas principales:** Detrás de la consola, utiliza las salidas **`MAIN OUTPUTS`** (conectores XLR macho balanceados de 3 pines o Jacks 1/4" TRS según el modelo).
* Lleva un cable XLR balanceado desde `MAIN OUT L` hacia el parlante izquierdo, y otro desde `MAIN OUT R` hacia el parlante derecho.

### La Regla de Oro de Encendido y Apagado (Evita quemar componentes):
> [!CAUTION]
> Un "pop" de encendido de la consola enviado a parlantes ya encendidos puede quemar los *tweeters* o diafragmas de agudos al instante.
* **Al ENCENDER:**
  1. Consola de audio primero.
  2. Equipos periféricos (PCs, reproductores).
  3. **Parlantes activos / Etapas de potencia AL FINAL.**
* **Al APAGAR:**
  1. **Parlantes activos / Etapas de potencia PRIMERO.**
  2. Consola de audio al final.

### Ajuste de Niveles en Vivo:
1. Coloca los dos faders grises de **`MAIN MIX` en 0 dB** (marca nominal).
2. Sube el volumen físico en la parte trasera de tus parlantes activos hasta el volumen general deseado para el salón o evento.
3. El control fino durante el evento se hace desde los faders de cada canal o desde los faders grises de la consola, sin necesidad de tocar los parlantes.
4. **Ecualizador Gráfico (FBQ / Graphic EQ):**
   * Si tu consola tiene ecualizador gráfico superior, mantenlo plano (todos los controles deslizantes al centro en 0).
   * Si un micrófono comienza a acoplarse (emitir un pitido de feedback), el sistema FBQ encenderá un led rojo en la frecuencia conflictiva; baja ligeramente ese deslizador para apagar el acople.

---

## 4. Conectar Música / Pistas desde el Celular

Existen dos métodos para conectar un teléfono o reproductor externo:

### Método A: Usar un Canal Estéreo con Fader (RECOMENDADO)
* **Cable necesario:** Jack 3.5mm estéreo (al celular) a **2 Jacks Plug 6.35mm (1/4" mono)**.
* **Conexión:** Conecta los dos plugs en las entradas de línea de un canal estéreo libre (por ejemplo, **Canales 7/8, 9/10 o 11/12** en las entradas rotuladas como `LINE IN L (MONO)` y `LINE IN R`).
* **Ventajas:**
  * Dispones de ecualización de agudos, medios y graves para la música.
  * Tienes un fader deslizante independiente para mezclar la música suavemente debajo de tu voz.
  * Presionas el botón **`MAIN`** de ese canal para enviarlo a los parlantes y a la PC al mismo tiempo.

### Método B: Usar las entradas RCA `CD/TAPE INPUT`
* **Cable necesario:** Jack 3.5mm a **2 conectores RCA rojo y blanco**.
* **Conexión:** Conecta a los conectores RCA etiquetados como **`CD/TAPE INPUT`** (NO output).
* **Cómo rutearlo:**
  * Si presionas el botón **`CD/TAPE TO MAIN`**, la música pasará directamente a la salida general.
  * **¡ADVERTENCIA DE BUCLE (LOOP)!** Si al mismo tiempo tienes la PC conectada a `CD/TAPE OUTPUT` grabando en Audition, la música del celular se grabará mezclada obligatoriamente con tu voz. Si la PC reproduce audio de vuelta a la consola, se creará un pitido de retroalimentación insoportable. Por esta razón, el **Método A** siempre es más seguro y profesional.

---

## 5. Resumen / Checklist Rápido "Anti-Errores"

Imprime o consulta esta lista rápida antes de cada sesión:

| Elemento / Control | Estado Correcto | Función / Razón |
| :--- | :--- | :--- |
| **LED Rojo Central (`MAIN SOLO / PFL`)** | **APAGADO** | Si está encendido, la consola está en modo prueba individual y los vúmetros no reflejan la salida real. |
| **Botón `SOLO` en los canales** | **LEVANTADO (Off)** | Salvo durante la prueba inicial para ajustar la ganancia. |
| **Botón `CD/TAPE TO MAIN`** | **LEVANTADO (Off)** | Evita cortar la salida de grabación o generar bucles parásitos con la PC. |
| **Cajita `SOURCE`** | **Solo `MAIN` presionado** | Asegura que el vúmetro y los audífonos escuchen la mezcla principal. |
| **Botón `MAIN` en cada canal usado** | **PRESIONADO (On)** | Asigna el canal al bus maestro de salida. |
| **Botón `SUB` en cada canal** | **LEVANTADO (Off)** | A menos que estés trabajando deliberadamente con submezclas. |
| **Botón `MUTE` en cada canal** | **APAGADO (Luz apagada)** | El canal debe estar activo para transmitir audio. |
| **Alimentación Phantom `+48V`** | **APAGADO para Shure Beta 58** | Solo encender si se conecta un micrófono de condensador. |
| **Faders de `MAIN MIX` (Grises)** | **En 0 dB** | Nivel nominal óptimo de salida. |
| **Jack de la PC** | **Jack AZUL trasero (Line In)** | El jack rosado es de micrófono amplificado y distorsionará la señal de la consola. |
