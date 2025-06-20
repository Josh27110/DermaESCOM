# DermaESCOM


Este es un proyecto full-stack de inteligencia artificial que utiliza un modelo de aprendizaje profundo para clasificar la severidad del acné a partir de una imagen. La aplicación web permite a los usuarios subir una foto o usar su cámara en vivo para recibir un análisis instantáneo y recomendaciones.

https://drive.google.com/file/d/12dYC1nGnDsAx9q0L04H-HOnX4Dg2sx-7/view?usp=sharing
TypeScript

https://drive.google.com/file/d/1c0JAjvPQ87mwe5MSeW_Gd2pSU9W9n6L5/view?usp=sharing
Python/Flask Server


---

## 🚀 Tecnologías Utilizadas

Este proyecto está dividido en dos partes principales: un backend para la IA y un frontend para la interfaz de usuario.

* **Backend (IA):**
    * **Python:** Lenguaje de programación principal.
    * **Flask:** Framework web para crear el servidor de la API.
    * **TensorFlow / Keras:** Para cargar y ejecutar el modelo de clasificación de imágenes.
    * **Pillow:** Para el preprocesamiento de imágenes.

* **Frontend (Interfaz de Usuario):**
    * **Next.js:** Framework de React para construir la aplicación web.
    * **React:** Biblioteca para construir la interfaz de usuario.
    * **TypeScript:** Para un código más robusto y seguro.
    * **Tailwind CSS & shadcn/ui:** Para el diseño y los componentes de la interfaz.

---

## 📋 Requisitos Previos

Antes de comenzar, asegúrate de tener instalado el siguiente software en tu sistema:

* **Python (versión 3.9 o superior):** [Descargar Python](https://www.python.org/downloads/)
* **Node.js (versión 18 o superior):** [Descargar Node.js](https://nodejs.org/)
* **PNPM (Opcional pero recomendado):** Gestor de paquetes para el proyecto de Node.js. Puedes instalarlo con `npm install -g pnpm`.

---

## 📂 Estructura del Proyecto

Para que la aplicación funcione, ambos proyectos (backend y frontend) deben estar en tu máquina. La estructura de carpetas recomendada es la siguiente:


proyecto-acne/
├── acne-classifier-app/   # Carpeta del Backend (Python/Flask)
│   ├── venv/
│   ├── app.py
│   └── acne_severity_model.keras
│
└── acne-analyzer-1/       # Carpeta del Frontend (Next.js)
├── app/
├── components/
└── package.json


---

## 🛠️ Configuración y Ejecución

Sigue estos pasos para configurar y ejecutar el proyecto localmente. Deberás tener dos terminales o ventanas de línea de comandos abiertas, una para el backend y otra para el frontend.

### **Paso 1: Configurar el Backend (Servidor de IA)**

1.  **Clona el repositorio** y navega a la carpeta del backend:
    ```bash
    cd ruta/hacia/acne-classifier-app
    ```

2.  **Crea y activa un entorno virtual:**
    ```bash
    # Crear el entorno virtual
    python -m venv venv

    # Activar en Windows
    .\venv\Scripts\activate

    # Activar en macOS/Linux
    source venv/bin/activate
    ```

3.  **Instala las dependencias de Python:**
    ```bash
    pip install Flask tensorflow numpy Pillow Flask-Cors
    ```

4.  **Coloca el modelo:** Asegúrate de que tu archivo de modelo entrenado, `acne_severity_model.keras`, esté dentro de esta carpeta (`acne-classifier-app`).

### **Paso 2: Configurar el Frontend (Interfaz de Usuario)**

1.  Abre una **nueva terminal** y navega a la carpeta del frontend:
    ```bash
    cd ruta/hacia/acne-analyzer-1
    ```

2.  **Instala las dependencias de Node.js:**
    ```bash
    pnpm install
    # o si usas npm: npm install
    ```

### **Paso 3: Ejecutar la Aplicación**

1.  **Inicia el Backend:** En la primera terminal (con el entorno virtual activado), ejecuta:
    ```bash
    flask run --host=0.0.0.0 --port=8080
    ```
    El servidor de IA estará ahora escuchando peticiones en el puerto 8080.

2.  **Inicia el Frontend:** En la segunda terminal, ejecuta:
    ```bash
    pnpm dev
    # o si usas npm: npm run dev
    ```
    La aplicación web estará ahora disponible en `http://localhost:3000`.

3.  **¡Prueba la aplicación!** Abre tu navegador web y ve a `http://localhost:3000`. Ya puedes subir una imagen o usar tu cámara para probar el analizador.

---

## ⚠️ Descargo de Responsabilidad

Esta herramienta es solo para fines informativos y educativos, y **no sustituye el consejo médico profesional**. Los resultados del análisis de IA no constituyen un diagnóstico médico. Para problemas de piel persistentes o graves, consulta siempre con un dermatólogo certificado o un profesional de la salud calificado.
