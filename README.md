# ArduArcade Matrix Game

Un mismo circuito muy simple para varios juegos arcade retro sobre Arduino Uno y matrices LED MAX7219. El enfoque del proyecto es educativo y maker: aprender, reutilizar hardware sencillo y construir una base arcade retro facil de montar y modificar.

## Idea

Este proyecto usa una unica base de hardware:

- Arduino Uno
- joystick analogico con pulsador
- matriz LED MAX7219 encadenada

Con ese mismo montaje se pueden cargar distintos juegos arcade guardados como variantes del sketch principal.

## Juegos incluidos

- Pong para 4 displays de 8x8 en [src/main.cpp](/home/javier/Tetris_LCD/src/main.cpp)
- Dodger en [src/main.cpp.dodger](/home/javier/Tetris_LCD/src/main.cpp.dodger)
- Shooter de nave en [src/main.cpp.shooter](/home/javier/Tetris_LCD/src/main.cpp.shooter)
- Snake en [src/main.cpp.snake](/home/javier/Tetris_LCD/src/main.cpp.snake)
- Sketch de pruebas en [src/main.cpp.test](/home/javier/Tetris_LCD/src/main.cpp.test)

## Hardware

- Arduino Uno
- 4 u 8 modulos MAX7219 de 8x8 segun el juego cargado
- joystick analogico
- cables Dupont
- fuente de 5V adecuada para la matriz LED

## Cableado base

MAX7219:

- `VCC` -> `5V`
- `GND` -> `GND`
- `DIN` -> `D11`
- `CS` / `LOAD` -> `D10`
- `CLK` -> `D13`

Joystick:

- `VCC` -> `5V`
- `GND` -> `GND`
- `VRX` -> `A0`
- `VRY` -> `A1`
- `SW` -> `D2` cuando el juego usa boton

Notas de montaje:

- Usa siempre masa comun entre Arduino, joystick y matriz.
- Si la matriz se comporta raro, revisa que estes entrando por el lado `IN` del primer modulo.
- Para varios modulos, alimenta la matriz con una fuente de 5V estable.

## Configuracion actual

- Entorno PlatformIO para `Arduino Uno`
- Libreria `MD_MAX72XX`
- Tipo de hardware de matriz: `FC16_HW`

## Compilar y subir

```bash
pio run
pio run -t upload --upload-port /dev/ttyACM0
```

## Usar con Arduino IDE

Si vas a cargar uno de estos sketches con el IDE de Arduino en lugar de PlatformIO:

- renombra el archivo principal de `main.cpp` a `nombre_del_sketch.ino`
- elimina la linea `#include <Arduino.h>` del encabezado

El IDE de Arduino genera ese include de forma implicita y espera trabajar con un archivo `.ino`, no con `.cpp`.

## Cambiar de juego

El sketch activo es siempre [src/main.cpp](/home/javier/Tetris_LCD/src/main.cpp).

Para cargar otro juego:

```bash
cp src/main.cpp.shooter src/main.cpp
pio run -t upload --upload-port /dev/ttyACM0
```

Sustituye `main.cpp.shooter` por `main.cpp.dodger`, `main.cpp.pong40`, `main.cpp.snake` o el archivo que quieras activar.

## Circuito

Aqui ira el esquema del circuito y el pinout final con imagenes.

## Video

Aqui ira el video del proyecto cuando este publicado.

## Galeria

Aqui iran fotos del montaje, la matriz y los juegos en funcionamiento.

## Enfoque del proyecto

Este repositorio esta pensado para:

- educacion tecnica y aprendizaje practico
- makers que quieran reutilizar un mismo circuito para varios juegos
- talleres, aulas y proyectos personales de electronica creativa
- experimentar con logica de juego, entradas analogicas y matrices LED

## Objetivo del proyecto

- Reutilizar un solo circuito para varios juegos
- Aprender logica de videojuegos sencillos en microcontroladores
- Crear una base educativa y maker facil de replicar
- Mantener una estetica arcade retro con hardware muy accesible
