# 📹 MoodSense — Detector de Ánimo (Web, Local)

## 🎯 Visión General y Objetivo

**MoodSense** es una aplicación web de una sola página diseñada para detectar expresiones faciales en tiempo real utilizando la cámara de tu dispositivo. El objetivo principal es ofrecer un análisis del estado de ánimo puramente local, sin enviar ningún dato de video o información personal a servidores externos, garantizando así la máxima privacidad del usuario.

La aplicación proporciona retroalimentación instantánea, un historial de emociones detectadas y un sistema de alerta temprana para contactar a una persona de apoyo si se detectan emociones negativas de forma sostenida.

## 🛠️ Pila Tecnológica (Cómo se hizo)

Este proyecto se construyó con un enfoque minimalista y de "privacidad por diseño", utilizando tecnologías web estándar que se ejecutan directamente en el navegador.

- **Arquitectura**: La aplicación completa está contenida en un único archivo `index.html`. No requiere un paso de compilación (`build`) ni dependencias de Node.js.
- **Lenguajes**:
    - **HTML5**: Para la estructura semántica del contenido.
    - **CSS3**: Para los estilos, utilizando un enfoque de tema oscuro con variables CSS para una fácil personalización.
    - **JavaScript (ES6+)**: Para toda la lógica funcional, desde la manipulación del DOM hasta la detección de emociones.
- **Frameworks y Librerías (cargados por CDN)**:
    - **Bootstrap 5.3**: Utilizado para la maquetación responsiva (Grid, Cards, Navbar) y los componentes de la interfaz de usuario (Modals, Toasts, Switches).
    - **@vladmandic/face-api.js**: Un fork de `face-api.js` que proporciona los modelos pre-entrenados para la detección de rostros y el análisis de expresiones faciales directamente en el navegador, potenciado por TensorFlow.js.
- **Almacenamiento**:
    - **`localStorage`**: Se utiliza para persistir el historial de detecciones y los datos del contacto de emergencia de forma local en el navegador del usuario.

## 🚀 Uso e Instrucciones

### Cómo ejecutar la aplicación
1.  Descarga el archivo `index.html`.
2.  Ábrelo directamente con un navegador web moderno (como Chrome, Firefox, Edge).
3.  **Importante**: Para que la cámara funcione, el navegador requiere un contexto seguro. Esto significa que debes acceder al archivo a través de un servidor local (`http://localhost/...`) o subirlo a un sitio con `https`
    - Una forma sencilla de crear un servidor local es usando la extensión "Live Server" en Visual Studio Code.

### Funcionalidades de la Interfaz

- **Iniciar / Detener Cámara**: Usa los botones en la barra de navegación para comenzar o detener la detección. La primera vez, el navegador te pedirá permiso para acceder a la cámara.
- **Visor**: Muestra la imagen de la cámara en tiempo real. Un recuadro se dibujará sobre el rostro detectado.
- **Controles**:
    - **Activar voz**: Anuncia la emoción detectada cuando cambia.
    - **Ocultar previsualización**: Oculta el video para mayor privacidad o para ahorrar recursos. La detección sigue funcionando.
    - **Auto-alerta familiar**: Activa o desactiva el sistema de monitoreo para el modal de SOS.
- **Estado**: Un badge en la esquina te informa de la emoción dominante y la confianza de la detección en tiempo real.
- **Contacto Familiar**:
    - Guarda el nombre y los números de teléfono/WhatsApp de un contacto de confianza. Esta información se almacena localmente y se usa para el sistema de alerta.
    - Los botones de prueba te permiten verificar que los enlaces `tel:` y `wa.me:` funcionan correctamente.
- **Historial**:
    - Muestra una tabla con las últimas 200 detecciones.
    - **Exportar CSV**: Descarga un archivo `.csv` con el historial *completo* de detecciones.
    - **Limpiar historial**: Borra todos los datos del historial del `localStorage`.

## 🔒 Privacidad

La privacidad es un pilar fundamental de esta aplicación.
- **Procesamiento 100% Local**: Ni el video de la cámara ni los datos de detección salen de tu dispositivo. Todo el análisis se realiza en tu navegador.
- **Sin Servidores**: La aplicación no se comunica con ningún servidor backend.
- **Almacenamiento Transparente**: Los datos (historial y contacto) se guardan en el `localStorage` de tu navegador, al cual solo tú tienes acceso. Puedes borrarlos en cualquier momento usando los botones de la aplicación o las herramientas de desarrollo de tu navegador.
