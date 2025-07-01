# Analizador de Severidad de Acné con Inteligencia Artificial

![Demostración de la Aplicación](https://i.imgur.com/gKj3a1C.png)

## 1. Resumen del Proyecto

Este proyecto es una aplicación web full-stack diseñada para analizar imágenes de la piel y clasificar la severidad del acné utilizando un modelo de aprendizaje profundo. El objetivo es proporcionar a los usuarios una herramienta accesible y rápida para obtener una evaluación inicial de su condición cutánea, junto con recomendaciones claras sobre los siguientes pasos a seguir.

### **El Problema**
El diagnóstico del acné y la determinación de su severidad pueden ser procesos subjetivos. Muchas personas no saben si su condición requiere un tratamiento de venta libre o una consulta profesional con un dermatólogo. Una herramienta de IA puede actuar como un primer filtro objetivo y educativo.

### **Nuestra Solución**
Desarrollamos una plataforma web interactiva donde un usuario puede:
* **Subir una foto** de su piel.
* **Usar su cámara en vivo** para una captura instantánea.
* Recibir un **diagnóstico de la severidad del acné** en una de cinco categorías.
* Obtener un **nivel de confianza** de la predicción y una **recomendación personalizada** basada en el diagnóstico.

---

## 2. El Cerebro del Proyecto: El Modelo de IA

El núcleo de esta aplicación es un modelo de **Red Neuronal Convolucional (CNN)**, un tipo de inteligencia artificial especializada en el procesamiento de imágenes.

### **¿Qué es una Red Neuronal?**
Una red neuronal es un sistema de computación inspirado en el cerebro humano. Consiste en "neuronas" digitales organizadas en capas. La información (en nuestro caso, los píxeles de una imagen) entra por la primera capa, es procesada a través de capas intermedias "ocultas" que reconocen patrones cada vez más complejos (bordes, texturas, formas, y finalmente, lesiones de acné), y produce un resultado en la capa final.

### **Arquitectura del Modelo: ResNet50**
Utilizamos **ResNet50**, una famosa y potente arquitectura de red neuronal con 50 capas de profundidad. La razón principal para elegirla es su uso de **Aprendizaje por Transferencia (Transfer Learning)**. ResNet50 ya fue pre-entrenada por Google con millones de imágenes, por lo que ya es experta en reconocer características visuales generales. Nosotros adaptamos este conocimiento para nuestra tarea específica.

La innovación clave de ResNet son las **conexiones residuales (skip connections)**, que resuelven el problema del "gradiente evanescente" en redes muy profundas, permitiendo que el entrenamiento sea más efectivo. Esto se logra con la fórmula:
$$ H(x) = F(x) + x $$
Donde la red aprende solo el "residuo" $F(x)$, facilitando el flujo de información y permitiendo la creación de modelos mucho más profundos y precisos.

---

## 3. El Proceso de Entrenamiento del Modelo

Nuestro modelo no se creó mágicamente; siguió un riguroso proceso de desarrollo:

1.  **Recopilación de Datos:** Combinamos imágenes de dos datasets públicos de Kaggle para crear un conjunto de datos robusto con 5 categorías: Piel Sana, Acné Leve, Moderado, Severo y Muy Severo.

2.  **Análisis Inicial y Desafíos:** El primer desafío fue un **desbalance de clases** severo: teníamos miles de imágenes de piel sana pero muy pocas de acné severo. Un modelo entrenado con estos datos sería propenso a ignorar las clases minoritarias.

3.  **Entrenamiento del Modelo Base:** Entrenamos un primer modelo usando aprendizaje por transferencia. Aunque alcanzó un 94% de exactitud, un análisis más profundo con una **matriz de confusión** reveló que el modelo era "tramposo": era excelente prediciendo "Piel Sana" pero muy malo diferenciando los niveles de acné.

4.  **Mejora y Ajuste Fino (Fine-Tuning):** Para solucionar los problemas, implementamos dos técnicas avanzadas:
    * **Pesos de Clase (Class Weights):** Modificamos el algoritmo de entrenamiento para que penalizara mucho más los errores en las clases con pocas imágenes. Esto forzó al modelo a prestar más atención a los casos de acné severo.
    * **Ajuste Fino:** "Descongelamos" las capas superiores de ResNet50 y las re-entrenamos con una tasa de aprendizaje muy baja, permitiendo que el modelo adaptara su conocimiento general a las características visuales específicas del acné.

El resultado fue un modelo mucho más equilibrado y preciso en las categorías que realmente importan.

---

## 4. Herramientas y Tecnologías Utilizadas

* **Backend (IA):**
    * **Python:** Lenguaje principal.
    * **TensorFlow/Keras:** Framework para construir y entrenar el modelo de IA.
    * **Flask:** Micro-framework para crear la API que sirve el modelo.
* **Frontend (Interfaz de Usuario):**
    * **Next.js / React:** Framework para construir la aplicación web interactiva.
    * **TypeScript:** Para un código más seguro y mantenible.
    * **Tailwind CSS & shadcn/ui:** Para un diseño moderno y componentes de UI.

---

## 5. Guía de Instalación y Ejecución Manual

Esta guía te permitirá ejecutar el proyecto completo en tu propia máquina.

### **Paso 1: Requisitos Previos**

Asegúrate de tener instalado el siguiente software:
* **Python (v3.9 o superior):** [Descargar Python](https://www.python.org/downloads/)
* **Node.js (v18 o superior):** [Descargar Node.js](https://nodejs.org/)
* **Git:** Para clonar el repositorio. [Descargar Git](https://git-scm.com/downloads).

### **Paso 2: Configuración del Proyecto**

1.  **Clona el repositorio:** Abre una terminal y ejecuta:
    ```bash
    git clone <URL_DE_TU_REPOSITORIO_GIT>
    cd <NOMBRE_DE_LA_CARPETA_DEL_PROYECTO>
    ```
   Omitir este paso, debido al peso del Keras, se proporcionan enlaces a un drive de Tanto el Front y el Back del Proyecto, ACNEIA4 contiene la parte del Back y acne-analyzer es el Front
   
2.  **Coloca el Modelo de IA:** Este es un paso manual y crucial.
    * Obtén el archivo del modelo entrenado: `acne_severity_model.keras`.
    * Colócalo dentro de la carpeta del backend. La ruta final debe ser: `<CARPETA_PROYECTO>/ACNEIA4/acne_severity_model.keras`.

### **Paso 3: Configuración del Backend (Python/Flask)**

1.  En tu terminal, navega a la carpeta del backend:
    ```bash
    cd ACNEIA4
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

### **Paso 4: Configuración del Frontend (Next.js)**

1.  Abre una **nueva terminal** y navega a la carpeta del frontend:
    ```bash
    cd <RUTA_A_LA_CARPETA_DEL_PROYECTO>/acne-analyzer-frontend
    ```
2.  **Instala las dependencias de Node.js:**
    ```bash
    npm install
    # o si usas pnpm: pnpm install
    ```

### **Paso 5: Ejecutar la Aplicación**

Ahora que todo está configurado, necesitarás dos terminales abiertas para ejecutar la aplicación.

1.  **Inicia el Backend:** En la primera terminal (con el entorno virtual `(venv)` activado), ejecuta:
    ```bash
    flask run --host=0.0.0.0 --port=8080
    ```
    El servidor de IA estará ahora escuchando peticiones. Deja esta terminal funcionando.

2.  **Inicia el Frontend:** En la segunda terminal, ejecuta:
    ```bash
    npm run dev
    # o si usas pnpm: pnpm dev
    ```
    La aplicación web estará ahora disponible en `http://localhost:3000`.

3.  **Prueba la aplicación:** Abre tu navegador web y ve a `http://localhost:3000`.

---

## 6. Descargo de Responsabilidad

Esta herramienta ha sido desarrollada con fines educativos y de demostración. **No es un dispositivo médico y no sustituye el diagnóstico, consejo o tratamiento de un profesional de la salud calificado.** Los resultados proporcionados por la IA son una evaluación basada en patrones y no deben ser considerados como un diagnóstico médico definitivo.
