# CompoStage

Cesto inteligente con IA que ensena a compostar jugando.

Sistema de clasificacion automatica de residuos que combina vision artificial y control fisico para educar a niños de jardin de infantes sobre el compostaje.

---

## Que hace

CompoStage clasifica residuos en dos categorias:

- COMPOSTABLE: restos organicos, cascaras, yerba, papel sin tinta
- NO COMPOSTABLE: plasticos, vidrio, metal, tetrapack, colillas

Cuando un niño acerca un residuo al cesto:

1. El sensor ultrasonico detecta el objeto a menos de 15 cm
2. La camara toma una foto automaticamente
3. La IA clasifica el residuo en milisegundos
4. El cesto reacciona con cara animada, voz amigable y movimiento fisico

---

## Como ejecutar

### Requisitos previos

- Python 3.12 (obligatorio, versiones 3.13+ no funcionan con TensorFlow)
- Windows 10/11, Linux o macOS
- 4 GB de RAM minimo (8 GB recomendado)
- Camara web o celular con camara

### Paso 1: Instalar Python

Descargar Python 3.12 desde python.org/downloads

Durante la instalacion:
- Marcar "Add Python to PATH"
- Marcar "Install for all users"

Verificar en CMD:
   python --version
Debe mostrar: Python 3.12.x

### Paso 2: Instalar dependencias

   pip install -r requirements.txt

### Paso 3: Ejecutar el servidor

   python app.py

Deberia mostrar:
   SERVIDOR COMPOSTAGE
   Interfaz USUARIO: http://localhost:5000/
   Interfaz DESARROLLADOR: http://localhost:5000/admin

### Paso 4: Abrir en el navegador

- Interfaz usuario: http://localhost:5000/
- Interfaz desarrollador: http://localhost:5000/admin

### Paso 5 (opcional): Probar desde el celular

1. Averiguar la IP de la PC:
   ipconfig

2. En el celular, abrir:
   http://IP_DE_LA_PC:5000/

---

## Componentes opcionales (hardware)

El sistema funciona sin hardware adicional, solo con la camara del dispositivo. Para la experiencia completa:

- Arduino UNO (controlador)
- Sensor HC-SR04 (detecta objeto a menos de 15 cm)
- Servo MG996R (abre y cierra la tapa)
- LED (indicador visual)

---

## Sobre la IA

- Arquitectura: MobileNetV2 con Transfer Learning
- Dataset: Waste Classification Data (Kaggle, 22000 imagenes)
- Formato: TensorFlow Lite (.tflite, 2.8 MB)
- Precision: 92 por ciento en validacion
- Latencia: 30 ms por inferencia
- Umbral de decision: 0.75

### Probar con una imagen

   python probar_ultimo.py ruta_a_imagen.jpg

---

## Estructura del proyecto

CompoStage/
  app.py
  modelo_compostable.tflite
  requirements.txt
  README.md
  templates/
    index.html
    admin.html
  static/
    faces/
    audios/

---

## Solucion de problemas

### Error: ModuleNotFoundError No module named X

   pip install -r requirements.txt

### La camara no funciona

- En PC: verificar que no este siendo usada por otra app
- En celular: usar Chrome o Edge

### Error: could not open port COMX

- Cambiar el puerto en app.py: PUERTO_ARDUINO = 'COM4'
- Cerrar el Monitor Serie del IDE de Arduino

---

## Versiones

- v0.1 (25/08/2026) - Primera IA (88 por ciento)
- v0.2 (24/09/2026) - Data augmentation (92 por ciento)
- v0.3 (28/09/2026) - Camara + servo
- v0.5 (02/10/2026) - Sensor ultrasonico
- v0.6 (05/10/2026) - Cara + voz
- v0.7 (07/10/2026) - Voz humana + 2 interfaces

---

## Proximas versiones

- v0.8 - Reentrenar con datasets reales
- v0.9 - Integrar celdas de carga (HX711)
- v1.0 - Prototipo final en cesto fisico

---

## Autor

ChivitaPro
CompoStage v0.7 - Octubre 2026

---

## Licencia

Proyecto de uso educativo para escuelas y concientizacion ambiental.
