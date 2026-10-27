# Desarrollo e Integración de soluciones VR - Proyecto final

**Aventura narrativa en realidad virtual inspirada en el universo de *Stranger Things*, con puzles, minijuegos e interacción con mandos y con seguimiento de manos.**

Es el proyecto final de la asignatura de Desarrollo e Integración de Soluciones de Realidad Virtual del máster. El jugador recorre escenas del pueblo y del *Upside Down*. En cada escena tiene que resolver puzles para avanzar, hasta llegar al final.

[![Vídeo de demostración](https://img.youtube.com/vi/w0qklUTVO1U/hqdefault.jpg)](https://youtu.be/w0qklUTVO1U)

## Enlaces

- 🎥 **Vídeo de demostración:** [youtu.be/w0qklUTVO1U](https://youtu.be/w0qklUTVO1U)


## Mi aportación

Fue un proyecto en grupo en el que cada integrante desarrolló varias escenas. Yo me encargué de dos escenas y de varios sistemas que se usan en todo el juego.

### Tutorial: exterior del instituto (`Tuto_ExteriorInstituto`)

Es la primera escena, donde el jugador aprende las mecánicas básicas.

- **Personaje guía (NPC):** cuando el jugador se acerca, el personaje se gira suavemente hacia él, lo sigue mediante **NavMesh** y le explica la situación con un audio (`AvatarAudioPlayer`, `PerseguirPlayer`).
- **Reloj de muñeca:** el jugador debe coger un reloj y colocarlo en su muñeca, que funciona como *socket* de XR Interaction Toolkit. Solo con el reloj puesto puede pulsar el botón que pone en marcha el cronómetro de la partida. Si no lo lleva, recibe un aviso sonoro (`StartContador`).

### Casa de Will (`CasaWill2`)

- **Juego de luces:** las luces de la pared se encienden siguiendo una secuencia aleatoria y el jugador tiene que pulsar el botón del color correspondiente. Con 10 aciertos seguidos se abre un portal; si falla, la secuencia vuelve a empezar (`JuegoLuces`, `ColorLuz`).
- **Puzle del dado:** el jugador lanza un dado con físicas y tiene que sacar un 3 para retirar las tablas que bloquean el paso. Para no frustrar al jugador, el 3 sale forzado tras varios intentos fallidos. Además, si el dado se aleja demasiado, vuelve automáticamente delante del jugador (`TirarDado`).
- **Oclusión de audio** para que el sonido se perciba de forma realista entre estancias (`AudioOcclusion`).
- **Socket en cabeza** para que el usuario pueda colocarse unos auriculares estilo retro que hacen que pueda escuchar "Running up that Hill", canción presente en la serie.
- **Hand tracking**. El usuario debe cambiar de mandos a hand tracking en un punto de esta escena para poder levitar y entrar en la casa de Will Bayers, donde continua la experiencia.

### Sistemas transversales

- **Cronómetro global:** un *ScriptableObject* guarda el tiempo de juego para que persista entre escenas y un *singleton* lo muestra en el reloj y guarda el tiempo final en un archivo (`GameTimerSO`, `TimeManager`, `ContarTiempoReloj`).
- **Reloj adaptable a mandos y manos:** el reloj de muñeca se coloca automáticamente según el jugador use mandos o seguimiento de manos (`WristSetupController`).
- **Levitación con seguimiento de manos:** tras mantener pulsado un botón, el jugador puede levitar, controlando la altura con la rotación de la palma derecha y el avance con la de la izquierda (`Levitacion`).

Todos mis scripts están en [`Assets/OlaiaScripts`](Assets/OlaiaScripts) y mis escenas en [`Assets/Scenes/Escenas/EscenasOlaia`](Assets/Scenes/Escenas/EscenasOlaia).

## Tecnologías

- **Unity 6** (6000.2) con Universal Render Pipeline
- **XR Interaction Toolkit**, **XR Hands** y **OpenXR**
- **Meta XR SDK** y **Meta Avatars SDK**
- **C#**, **Shader Graph**, **NavMesh** y el nuevo **Input System**
- **DOTween** para animaciones
- **Git y GitHub** para el trabajo en equipo

## Equipo

| Integrante | Escenas |
|---|---|
| **Olaia Picabea** | Tutorial en el exterior del instituto y Casa de Will, además de los sistemas transversales |
| Álvaro | Baños del instituto (normal y *Upside Down*), Castillo Byers |
| Alex | Arcade, sótano del arcade, Hangar, bosque final |
