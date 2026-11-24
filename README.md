# AR Tour Kaminaljuyú (iOS)

## Descripción

Aplicación iOS de realidad aumentada para el recorrido guiado del Parque Arqueológico
Kaminaljuyú, en Guatemala. La aplicación acompaña al visitante a lo largo de los
montículos del parque usando su ubicación GPS, muestra modelos 3D de las estructuras
sobre la cámara del dispositivo y lo guía con videos pregrabados de un guía virtual en
español o inglés.

Es una migración y mejora de una versión previa para Android, desarrollada como trabajo
de graduación en la Universidad del Valle de Guatemala (2026).

Funcionalidades principales:

- Tour guiado por los puntos de interés del parque, con detección de proximidad por GPS.
- Realidad aumentada con modelos 3D de los montículos y una flecha que indica la
  dirección del siguiente punto.
- Guía virtual con videos pregrabados y subtítulos, activados por distancia al montículo.
- Mapa con la ruta del recorrido, alternable con el video del guía.
- Soporte completo para español e inglés (textos, videos y subtítulos).
- Instrucciones de uso y términos y condiciones integrados.

## Tecnologías utilizadas

| Área | Tecnología |
|---|---|
| Lenguaje | Swift 5 |
| Interfaz | SwiftUI (UIKit en la vista de realidad aumentada) |
| Estado y eventos | Combine |
| Ubicación | CoreLocation |
| Mapa | Google Maps SDK para iOS |
| Realidad aumentada | ARKit + SceneKit |
| Video | AVFoundation / AVKit |
| Gestor de dependencias | CocoaPods |
| Pruebas | Swift Testing |

## Requisitos previos

- **macOS** con **Xcode 26** o superior.
- **CocoaPods** instalado:
  ```bash
  sudo gem install cocoapods
  ```
  o bien:
  ```bash
  brew install cocoapods
  ```
- **iPhone físico con iOS 26.0 o superior.** La realidad aumentada no funciona en el
  simulador porque ARKit requiere la cámara y los sensores del dispositivo real.
- **API Key de Google Maps** con el SDK de Maps para iOS habilitado. Se puede obtener
  en: <https://console.cloud.google.com/google/maps-apis>.

## Instalación

1. **Clonar el repositorio:**

   ```bash
   git clone https://github.com/SRV-JSPA/2026-22318-jose-santiago-pereira-alvarado.git
   cd 2026-22318-jose-santiago-pereira-alvarado/src
   ```

2. **Instalar las dependencias (CocoaPods):**

   ```bash
   pod install
   ```

   Esto descarga el Google Maps SDK y genera la carpeta `Pods/` (excluida del
   repositorio por `.gitignore`).

3. **Configurar las variables de entorno.** En este proyecto iOS las variables se
   definen en un archivo `.xcconfig`. En `/src` se incluye `.env.example` como
   referencia general y `Secrets.xcconfig.example` como plantilla real:

   ```bash
   cp .env.example .env
   cp Secrets.xcconfig.example Secrets.xcconfig
   ```

   Luego, editar `Secrets.xcconfig` y reemplazar el placeholder con la API Key real:

   ```
   GOOGLE_MAPS_API_KEY = tu_api_key_real
   ```

   > `Secrets.xcconfig` y `.env` están en `.gitignore` y nunca deben subirse al
   > repositorio.

4. **Abrir el workspace en Xcode** (no el `.xcodeproj`, porque las dependencias de
   CocoaPods solo se cargan desde el workspace):

   ```bash
   open ArTourKaminaljuyu.xcworkspace
   ```

5. **Configurar firma:** en *Signing & Capabilities*, seleccionar un equipo de
   desarrollo y, si es necesario, cambiar el *Bundle Identifier*.

6. **Ejecutar:** conectar el iPhone, seleccionarlo como destino de compilación y
   presionar ⌘R. La primera vez, aceptar los permisos de cámara y ubicación.

### Ejecución de pruebas

Desde Xcode: **⌘U**. Desde la terminal:

```bash
xcodebuild test \
  -workspace ArTourKaminaljuyu.xcworkspace \
  -scheme ArTourKaminaljuyu \
  -destination 'platform=iOS Simulator,name=iPhone 15'
```

## Capturas

Las capturas de pantalla de la aplicación se encuentran en la carpeta
[`/capturas`](./capturas). El proyecto incluye **16 capturas** (`captura-01.png` a
`captura-16.png`) que documentan las pantallas y el flujo principal de la aplicación.

## Demo

El video demostrativo del funcionamiento de la aplicación está en
[`/demo/demo.mp4`](./demo/demo.mp4).

## Documentación

- **Informe final del trabajo de graduación:**
  [`/docs/informe_final.pdf`](./docs/informe_final.pdf)
- **Consentimiento firmado:**
  [`/docs/consentimiento_firmado.pdf`](./docs/consentimiento_firmado.pdf)

## Autores

Universidad del Valle de Guatemala — Facultad de Ingeniería, 2026.

| Nombre | Carné | Módulo |
|---|---|---|
| Jose Santiago Pereira Alvarado | 22318 | Módulo de GPS |
| Mónica Alejandra Salvatierra Chacón | 22249 | Arquitectura, integración, módulo de lenguaje e interfaz |
| Andre Yatmian Jo Mai | 22199 | Módulo de realidad aumentada |
| Nancy Gabriela Mazariegos Molina | 22513 | Módulo de guía virtual |

## Licencia

Sin licencia.
