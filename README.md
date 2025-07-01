# DermoScan AI: Sistema de Detección de Melanoma con IA

Una aplicación web de extremo a extremo que aprovecha el aprendizaje profundo para realizar análisis en tiempo real de imágenes de lesiones cutáneas para la detección preliminar de melanoma. Esta herramienta proporciona una interfaz intuitiva para que los usuarios obtengan una evaluación instantánea impulsada por inteligencia artificial.

---

## 📜 Descripción del Proyecto

Este proyecto representa un ciclo de vida completo de machine learning. Comenzó con la adquisición de un conjunto de datos de imágenes médicas (HAM10000), seguido del entrenamiento de un modelo de aprendizaje profundo en un entorno de nube con GPU. El modelo entrenado se sirve a través de una API REST de Python/Flask. Finalmente, una interfaz de usuario moderna y responsiva, construida con Next.js y TypeScript, se comunica con el backend para ofrecer una experiencia de usuario fluida.

---

## ✨ Características Principales

-   **Análisis con IA en tiempo real**: Utiliza un modelo **ResNet50** entrenado para clasificar lesiones cutáneas.
-   **Doble método de entrada de imagen**: Permite a los usuarios **cargar un archivo** de imagen o usar la **cámara del dispositivo** para una captura en vivo.
-   **Clasificación Binaria**: Clasifica las lesiones como **Benigno** (no canceroso) o **Maligno** (potencialmente canceroso).
-   **Interfaz de Usuario Dinámica**: Los resultados se codifican por colores (🟢 Verde para Benigno, 🔴 Rojo para Maligno) para una comprensión inmediata.
-   **Diseño Responsivo**: Totalmente funcional en computadoras de escritorio y dispositivos móviles.
-   **Interfaz en Español**: Toda la UI está presentada en español.

---

## 🛠️ Tecnologías Utilizadas

### **Frontend (Interfaz de Usuario)**
-   **Framework**: Next.js (App Router)
-   **Lenguaje**: TypeScript
-   **Estilos**: Tailwind CSS
-   **Componentes**: shadcn/ui (generado por v0.dev)

### **Backend (API del Modelo)**
-   **Framework**: Python / Flask
-   **Librerías Clave**: Flask-Cors, Pillow, NumPy

### **IA y Machine Learning**
-   **Arquitectura**: ResNet50 (usando Transfer Learning)
-   **Framework**: TensorFlow / Keras
-   **Dataset**: HAM10000
-   **Entorno de Entrenamiento**: Google Colab con GPU

---

## 🚀 Instalación y Configuración

Esta guía te llevará a través de todo el proceso, desde la instalación de las herramientas base hasta la ejecución de la aplicación.

### **Paso 1: Instalar Requisitos Previos (si no los tienes)**

#### **Python**
El backend está construido con Python.
1.  **Descarga Python**: Ve al [sitio web oficial de Python](https://www.python.org/downloads/) y descarga un instalador para la versión 3.8 o superior.
2.  **Instala Python**: Ejecuta el instalador. **Importante:** Durante la instalación en Windows, asegúrate de marcar la casilla que dice **"Add Python to PATH"**.
3.  **Verifica la instalación**: Abre una nueva terminal y escribe `python --version`. Deberías ver la versión que instalaste.

#### **Node.js y npm**
El frontend requiere Node.js, que incluye el manejador de paquetes `npm`.
1.  **Descarga Node.js**: Ve al [sitio web oficial de Node.js](https://nodejs.org/) y descarga la versión **LTS** (Long Term Support).
2.  **Instala Node.js**: Ejecuta el instalador, aceptando las opciones por defecto.
3.  **Verifica la instalación**: Abre una nueva terminal y ejecuta `node -v` y `npm -v`. Deberías ver las versiones de cada herramienta.

### **Paso 2: Configurar el Backend (Python)**

1.  **Navega a la carpeta del backend** en tu terminal:
    ```bash
    cd melanoma-backend
    ```

2.  **Crea y activa un entorno virtual**. Esto crea un espacio aislado para las librerías de Python de este proyecto.
    ```bash
    # Crear el entorno
    python -m venv venv

    # Activar en Windows
    .\venv\Scripts\activate

    # Activar en macOS/Linux
    source venv/bin/activate
    ```
    *(Verás `(venv)` al inicio de la línea en tu terminal si se activó correctamente)*

3.  **Instala las librerías de Python** desde el archivo `requirements.txt`:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Ejecuta el servidor de Flask**:
    ```bash
    python app.py
    ```
    El backend ahora estará corriendo en `http://127.0.0.1:8080`. **Mantén esta terminal abierta.**

### **Paso 3: Configurar el Frontend (Next.js)**

1.  **Abre una segunda terminal.**

2.  **Navega a la carpeta del frontend:**
    ```bash
    cd melanoma-frontend
    ```

3.  **Instala `pnpm` globalmente** (manejador de paquetes rápido):
    ```bash
    npm install -g pnpm
    ```

4.  **Instala las dependencias del proyecto:**
    ```bash
    pnpm install
    ```

5.  **Ejecuta el servidor de desarrollo de Next.js:**
    ```bash
    pnpm dev
    ```
    El frontend ahora estará corriendo en `http://localhost:3000`. **Mantén esta segunda terminal abierta.**

---

## 💻 Uso de la Aplicación

1.  Con ambos servidores corriendo, abre tu navegador web.
2.  Ve a la dirección del frontend: `http://localhost:3000`.
3.  Usa los botones "Subir Imagen" o "Usar Cámara Web" para proporcionar una imagen y recibir el análisis.

---

## ⚠️ Descargo de Responsabilidad Médica

Esta herramienta de diagnóstico por IA está destinada únicamente para fines educativos y de detección. **No** constituye un consejo, diagnóstico o tratamiento médico profesional. Todos los resultados deben ser validados por un profesional de la salud calificado. Si tienes alguna lesión o síntoma preocupante, consulta inmediatamente con un dermatólogo certificado.
