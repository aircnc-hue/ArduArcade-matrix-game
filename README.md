# ArduArcade Matrix Game

Varios juegos arcade retro en una sola base de hardware: Arduino Uno, joystick analogico y matriz MAX7219. El proyecto esta pensado para educacion, talleres y makers que quieran aprender logica de juego, entradas analogicas y electronica sencilla sin cambiar de circuito cada vez.

## Que es

La idea es simple: un mismo montaje fisico, varios juegos cargables.

- una base comun con Arduino Uno
- joystick analogico con pulsador
- matriz LED MAX7219 encadenada
- sketches intercambiables para probar juegos distintos

Esto permite usar el proyecto como banco de pruebas, actividad educativa o mini arcade retro de sobremesa.

## Para quien es

- educacion tecnica y aprendizaje practico
- makers que quieran reutilizar el mismo circuito
- talleres de electronica creativa
- personas que quieran empezar con juegos simples en microcontroladores

## Juegos incluidos

| Juego | Archivo | Descripcion |
| --- | --- | --- |
| Pong | [src/main.cpp](/home/javier/Tetris_LCD/src/main.cpp) | Version activa. Pensada para 4 displays de 8x8, con marcador y sets. |
| Dodger | [src/main.cpp.dodger](/home/javier/Tetris_LCD/src/main.cpp.dodger) | Esquiva obstaculos, con dash, vidas y aumento de dificultad. |
| Shooter | [src/main.cpp.shooter](/home/javier/Tetris_LCD/src/main.cpp.shooter) | Nave lateral con disparos, enemigos y marcador dedicado. |
| Snake | [src/main.cpp.snake](/home/javier/Tetris_LCD/src/main.cpp.snake) | Variante de Snake para matriz LED. |
| Test | [src/main.cpp.test](/home/javier/Tetris_LCD/src/main.cpp.test) | Verificacion de joystick, orientacion y matriz antes de jugar. |

## Hardware base

- Arduino Uno
- 4 u 8 modulos MAX7219 de 8x8, segun el juego cargado
- joystick analogico con pulsador
- cables Dupont
- fuente de 5V estable para la matriz LED

## Conexion rapida

### Matriz MAX7219

| Modulo | Arduino Uno |
| --- | --- |
| VCC | 5V |
| GND | GND |
| DIN | D11 |
| CS / LOAD | D10 |
| CLK | D13 |

### Joystick

| Joystick | Arduino Uno |
| --- | --- |
| VCC | 5V |
| GND | GND |
| VRX | A0 |
| VRY | A1 |
| SW | D2 |

## Notas de montaje

- Usa siempre masa comun entre Arduino, joystick y matriz.
- Conecta el primer modulo MAX7219 por el lado `IN`.
- Si usas varios modulos, alimenta la matriz con una fuente de 5V estable.
- Si la imagen sale rara, revisa orientacion, orden fisico de los modulos y tipo de hardware.

## Configuracion del proyecto

- placa objetivo: `Arduino Uno`
- entorno: `PlatformIO`
- libreria principal: `MD_MAX72XX`
- tipo de hardware configurado: `FC16_HW`

## Compilar y subir con PlatformIO

```bash
pio run
pio run -t upload --upload-port /dev/ttyACM0
```

## Usar con Arduino IDE

Si prefieres cargar los sketches con Arduino IDE en lugar de PlatformIO:

1. Renombra el archivo principal de `main.cpp` a `nombre_del_sketch.ino`.
2. Elimina la linea `#include <Arduino.h>` del encabezado.

Arduino IDE agrega ese include de forma implicita y trabaja sobre archivos `.ino`, no sobre `.cpp`.

## Cambiar de juego

El sketch activo es siempre [src/main.cpp](/home/javier/Tetris_LCD/src/main.cpp).

Para activar otro juego desde terminal:

```bash
cp src/main.cpp.shooter src/main.cpp
pio run -t upload --upload-port /dev/ttyACM0
```

Puedes sustituir `main.cpp.shooter` por `main.cpp.dodger`, `main.cpp.pong40`, `main.cpp.snake` o `main.cpp.test`.

## Flujo recomendado

1. Empieza con [src/main.cpp.test](/home/javier/Tetris_LCD/src/main.cpp.test) para comprobar joystick y orientacion.
2. Cuando el hardware responda bien, carga el juego que quieras.
3. Ajusta cantidad de modulos y constantes del sketch si cambias de matriz.

## Circuito

Aqui ira el esquema electrico final y el pinout visual del montaje.

## Video

Aqui ira el video del proyecto en funcionamiento.

## Galeria

Aqui iran imagenes del circuito, la matriz y los distintos juegos cargados.

## Objetivo

- reutilizar un solo circuito para varios juegos arcade retro
- aprender programacion y electronica de forma visual y practica
- ofrecer una base sencilla para educacion y makers
- mantener una estetica retro con hardware economico y accesible
