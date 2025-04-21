Coach CV
Descripción General

Coach CV es una plataforma moderna para entrenadores deportivos, instructores y mentores que desean crear, gestionar y compartir sus perfiles profesionales en línea. Esta herramienta permite construir currículums atractivos enfocados en las necesidades específicas del ámbito del coaching.
Características Principales

    Plantillas profesionales optimizadas para perfiles de entrenadores

    Secciones especializadas para certificaciones, logros y metodologías

    Opciones para destacar resultados con clientes/equipos anteriores

    Compartición directa en plataformas profesionales y redes sociales

    Estadísticas de visualización del perfil

Instalación
Requisitos Previos

    Node.js (v14.0 o superior)

    NPM (v6.0 o superior)

    MongoDB (v4.4 o superior)

Pasos de Instalación

    Clone el repositorio

    git clone https://github.com/your-username/coach-cv.git
    cd coach-cv

    Instale las dependencias

    npm install

    Configure las variables de entorno

    cp .env.example .env

    Edite el archivo

    .env

    con sus configuraciones


    Inicie la aplicación

    npm run dev

Uso

    Regístrese con su correo electrónico o inicie sesión con sus credenciales

    Seleccione una plantilla para su CV

    Complete las diferentes secciones del perfil

    Personalice colores, fuentes y disposición

    Publique y comparta su Coach CV mediante el enlace generado

Configuración Avanzada

Consulte la documentación completa para opciones de configuración avanzada, integración con APIs externas y personalización adicional.
Contribución

Las contribuciones son bienvenidas. Por favor, revise nuestras guías de contribución antes de enviar pull requests.
Licencia

Este proyecto está licenciado bajo MIT License.
Soporte

Si encuentra algún problema o tiene preguntas, por favor:

    Revise los problemas existentes

    Abra un nuevo issue si su problema no está reportado

    Contacte al equipo en support@coachcv.com

Desarrollado con ❤️ para la comunidad de coaches profesionales# 📋 Coach CV

Flask React Python Material UI License

Coach CV es un chatbot inteligente que analiza currículums en tiempo real y ofrece recomendaciones personalizadas según el rol profesional objetivo. Utiliza tecnologías de procesamiento de lenguaje natural para identificar puntos de mejora, palabras clave faltantes y optimizar la estructura del CV.
📑 Contenido

    Características principales

    Arquitectura

    Stack tecnológico

    Requisitos previos

    Estructura del proyecto

    Instalación y configuración

    Desarrollo local

    Despliegue

    Contribución

    Licencia

✨ Características principales

    📄 Análisis de documentos - Soporte para formatos PDF y Word (límite 5 MB)

    🎯 Recomendaciones personalizadas - Sugerencias específicas según el rol profesional

    🔍 Detección de palabras clave - Identifica términos relevantes faltantes por industria

    📊 Análisis de estructura - Evalúa secciones, longitud y formato del CV

    💡 Sugerencias de mejora - Recomienda cambios para logros cuantificables y voz activa

    🔄 Interfaz interactiva - Resalta errores y mejoras con códigos de color

    📱 Diseño responsive - Funciona en dispositivos móviles y escritorio

🏗️ Arquitectura

sequenceDiagram
    participant Usuario
    participant Frontend as React Frontend
    participant Backend as Flask API
    participant Parser as CV Parser
    participant NLP as Módulo NLP
    participant DB as Almacenamiento
    
    Usuario->>Frontend: Sube CV + Selecciona rol
    Frontend->>Backend: Envía documento (PDF/Word)
    Backend->>Parser: Procesa documento
    Parser->>Backend: Extrae texto estructurado
    Backend->>NLP: Envía texto + rol
    
    alt Usando spaCy
        NLP->>NLP: Análisis NER + Reglas
    else Usando GPT
        NLP->>NLP: Envía prompt a GPT API
    end
    
    NLP->>Backend: Retorna análisis y sugerencias
    Backend->>DB: Guarda resultados (opcional)
    Backend->>Frontend: Devuelve recomendaciones JSON
    Frontend->>Usuario: Muestra interfaz de feedback

💻 Stack tecnológico
Frontend

    React - Biblioteca JavaScript para construir interfaces de usuario

    Material-UI - Framework de diseño para componentes React

    react-dropzone - Soporte para drag-and-drop de archivos

    axios - Cliente HTTP para realizar peticiones al backend

Backend

    Flask - Framework web ligero para Python

    PyMuPDF - Extracción de texto de documentos PDF

    python-docx - Procesamiento de documentos Word

    spaCy - Biblioteca de procesamiento de lenguaje natural

    OpenAI API (opcional) - Para análisis avanzado con GPT-3.5/4

Almacenamiento

    SQLite - Base de datos ligera para almacenamiento local

    Firebase Storage (opcional) - Para almacenamiento en la nube

Infraestructura

    Render/PythonAnywhere - Hosting para el backend Flask

    Vercel/GitHub Pages - Despliegue del frontend React

    GitHub Actions - CI/CD para automatización de despliegue

📋 Requisitos previos

Para desarrollar y ejecutar este proyecto localmente, necesitarás:

    Python (v3.9+)

    Node.js (v14+)

    npm o yarn

    Git

    Cuenta en OpenAI (opcional, para GPT-3.5/4)

📁 Estructura del proyecto

coach-cv/
├── frontend/                  # Aplicación React con Material-UI
│   ├── public/
│   ├── src/
│   │   ├── components/        # Componentes React
│   │   ├── context/           # Context API para estado global
│   │   ├── hooks/             # Custom hooks React
│   │   ├── pages/             # Páginas principales
│   │   ├── services/          # Servicios para API
│   │   ├── utils/             # Funciones utilidad
│   │   ├── App.js
│   │   └── index.js
│   ├── package.json
│   └── README.md
│
├── backend/                   # API Flask para procesamiento
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py            # Punto de entrada
│   │   ├── cv_parser.py       # Extracción de texto
│   │   ├── suggestions.py     # Motor de recomendaciones
│   │   └── config.py          # Configuraciones
│   ├── mock_api/              # Mock responses para desarrollo
│   │   └── mock_gpt.py
│   ├── requirements.txt
│   ├── Dockerfile
│   └── .env.example
│
├── samples/                   # CVs de ejemplo para testing
│   └── cv_test.pdf
│
├── docs/                      # Documentación adicional
├── .github/                   # Workflows para GitHub Actions
├── .gitignore
├── README.md
└── LICENSE

🔧 Instalación y configuración
1. Clonar el repositorio

git clone https://github.com/usuario/coach-cv.git
cd coach-cv

2. Configurar el backend

# Entrar al directorio backend
cd backend

# Crear entorno virtual
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# Instalar dependencias
pip install -r requirements.txt

# Copiar archivo de variables de entorno y configurar (si se usa OpenAI)
cp .env.example .env
# Editar .env con tu API key de OpenAI si es necesario

3. Configurar el frontend

# Entrar al directorio frontend
cd ../frontend

# Instalar dependencias
npm install
# o con yarn
yarn install

# Copiar archivo de variables de entorno y configurar
cp .env.example .env.local
# Editar .env.local con la URL del backend

💻 Desarrollo local
Ejecutar el backend

# En el directorio /backend con el entorno virtual activado
export FLASK_APP=app/main.py
export FLASK_ENV=development
flask run

El servidor Flask estará disponible en http://localhost:5000
Ejecutar el frontend

# En el directorio /frontend
npm start
# o con yarn
yarn start

La aplicación React estará disponible en http://localhost:3000
Probar con datos de ejemplo

El proyecto incluye archivos de ejemplo en la carpeta

samples/

que puedes usar para probar la funcionalidad:


# Usando curl para probar el endpoint del backend
curl -X POST -F "file=@samples/cv_test.pdf" -F "role=developer" http://localhost:5000/analyze-cv

🚀 Despliegue
Despliegue del backend
Opción 1: PythonAnywhere

    Crear una cuenta en PythonAnywhere

    Subir el código del backend

    Configurar una aplicación web Flask siguiendo la documentación oficial

Opción 2: Render

    Crear una cuenta en Render

    Conectar tu repositorio de GitHub

    Crear un nuevo Web Service, seleccionando el repositorio

    Configurar como tipo "Python", y el comando de inicio

    gunicorn app.main:app

Despliegue del frontend
Opción 1: Vercel

    Crear una cuenta en Vercel

    Importar tu repositorio desde GitHub

    Configurar las variables de entorno necesarias

    Desplegar automáticamente cuando haces push a la rama principal

Opción 2: GitHub Pages

    Instalar

    gh-pages

    en el proyecto:

    npm install --save-dev gh-pages

    Añadir estos scripts a

    package.json

    :

    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"

    Desplegar con:

    npm run deploy

📋 Flujo de trabajo

graph TD
    A[Usuario sube CV] --> B[Extracción de texto]
    B --> C[Detección de secciones]
    C --> D[Análisis NLP]
    D --> E{Rol seleccionado}
    E -->|Desarrollador| F[Verificar keywords técnicas]
    E -->|Data Scientist| G[Verificar skills analíticas]
    E -->|General| H[Verificar estructura básica]
    F --> I[Generar recomendaciones]
    G --> I
    H --> I
    I --> J[Mostrar feedback al usuario]

👥 Contribución

Las contribuciones son bienvenidas. Por favor, sigue estos pasos:

    Haz fork del proyecto

    Crea una rama para tu característica (

    git checkout -b feature/amazing-feature

    )

    Haz commit de tus cambios (

    git commit -m 'Add some amazing feature'

    )

    Haz push a la rama (

    git push origin feature/amazing-feature

    )

    Abre un Pull Request

📄 Licencia

Este proyecto está licenciado bajo la Licencia MIT - ver el archivo LICENSE para más detalles.
