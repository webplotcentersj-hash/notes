# Ale Notes 📝

Una aplicación de notas avanzada construida con React y Vite, con soporte para múltiples tipos de bloques y sincronización con Supabase.

## ✨ Características

- **Múltiples tipos de bloques:**
  - Texto simple
  - Columnas (dos columnas)
  - Tablas editables
  - Tableros Kanban
  - Planes de proyecto con tareas
  - Listas especiales (libros, series, viajes, deportes, etc.)
  - Imágenes con leyendas

- **Organización:**
  - Proyectos con colores personalizables
  - Búsqueda de notas
  - Galería global de imágenes
  - Categorización por proyectos

- **Sincronización:**
  - Guardado automático
  - Soporte para Supabase (producción)
  - Fallback a LocalStorage (desarrollo)

- **Diseño:**
  - Interfaz moderna y responsive
  - Optimizado para móviles y tablets
  - Animaciones suaves
  - Tema claro

## 🚀 Inicio Rápido

### Prerrequisitos

- Node.js 18+ y npm/yarn/pnpm

### Instalación

1. Clona o descarga el proyecto
2. Instala las dependencias:

```bash
npm install
```

3. (Opcional) Configura Supabase para producción:
   - Crea un archivo `.env.local` basado en `.env.example`
   - Completa tus credenciales de Supabase
   - Ejecuta el script SQL en Supabase (`supabase-setup.sql`)

4. Inicia el servidor de desarrollo:

```bash
npm run dev
```

La aplicación estará disponible en `http://localhost:3000`

## 📦 Construcción para Producción

```bash
npm run build
```

Los archivos compilados estarán en la carpeta `dist/`.

Para previsualizar la build:

```bash
npm run preview
```

## 🔧 Configuración de Supabase

### Paso 1: Crear proyecto en Supabase

1. Ve a [supabase.com](https://supabase.com) y crea una cuenta/proyecto
2. Obtén tu URL y clave anónima desde Settings > API

### Paso 2: Configurar variables de entorno

Crea un archivo `.env.local` en la raíz del proyecto:

```env
VITE_SUPABASE_URL=https://tu-proyecto.supabase.co
VITE_SUPABASE_ANON_KEY=tu_clave_anonima_aqui
```

### Paso 3: Ejecutar script SQL

1. Ve al SQL Editor en tu proyecto Supabase
2. Copia y ejecuta el contenido de `supabase-setup.sql`
3. Esto creará las tablas necesarias y configurará las políticas de seguridad

### Paso 4: Verificar

Una vez configurado, la aplicación usará automáticamente Supabase en lugar de LocalStorage.

## 📁 Estructura del Proyecto

```
Notes/
├── src/
│   ├── App.jsx          # Componente principal
│   ├── main.jsx         # Punto de entrada
│   └── index.css        # Estilos globales y Tailwind
├── index.html           # HTML principal
├── package.json         # Dependencias y scripts
├── vite.config.js       # Configuración de Vite
├── tailwind.config.js   # Configuración de Tailwind
├── postcss.config.js    # Configuración de PostCSS
├── supabase-setup.sql  # Script SQL para Supabase
├── .env.example         # Ejemplo de variables de entorno
└── README.md           # Este archivo
```

## 🛠️ Tecnologías Utilizadas

- **React 18** - Biblioteca UI
- **Vite** - Build tool y dev server
- **Tailwind CSS** - Estilos
- **Lucide React** - Iconos
- **Supabase** - Backend y base de datos (opcional)

## 📝 Notas de Desarrollo

- El código está preparado para funcionar con o sin Supabase
- Si no hay credenciales de Supabase, usa LocalStorage automáticamente
- El guardado automático tiene un delay de 1 segundo para evitar demasiadas escrituras
- Las imágenes se almacenan como base64 (considera usar Supabase Storage para producción)

## 🚢 Despliegue en Vercel

### Opción 1: Desde GitHub/GitLab/Bitbucket

1. **Sube tu código a un repositorio Git** (GitHub, GitLab, o Bitbucket)

2. **Conecta el repositorio a Vercel:**
   - Ve a [vercel.com](https://vercel.com) e inicia sesión
   - Haz clic en "Add New Project"
   - Importa tu repositorio
   - Vercel detectará automáticamente que es un proyecto Vite

3. **Configura las variables de entorno:**
   - En la configuración del proyecto, ve a "Environment Variables"
   - Agrega:
     - `VITE_SUPABASE_URL` = tu URL de Supabase
     - `VITE_SUPABASE_ANON_KEY` = tu clave anónima de Supabase
   - Asegúrate de que estén configuradas para "Production", "Preview" y "Development"

4. **Despliega:**
   - Haz clic en "Deploy"
   - Vercel construirá y desplegará automáticamente

### Opción 2: Desde la línea de comandos

1. **Instala Vercel CLI:**
   ```bash
   npm i -g vercel
   ```

2. **Inicia sesión:**
   ```bash
   vercel login
   ```

3. **Despliega:**
   ```bash
   vercel
   ```
   - Sigue las instrucciones en pantalla
   - Cuando te pregunte por las variables de entorno, agrégalas

4. **Para producción:**
   ```bash
   vercel --prod
   ```

### Configuración automática

El proyecto incluye un archivo `vercel.json` que configura automáticamente:
- Framework: Vite
- Build command: `npm run build`
- Output directory: `dist`
- Rewrites para SPA (Single Page Application)

### Notas importantes

- ✅ Vercel detecta automáticamente proyectos Vite
- ✅ Las variables de entorno deben empezar con `VITE_` para que Vite las incluya en el build
- ✅ El archivo `vercel.json` ya está configurado para rutas SPA
- ✅ Si no configuras Supabase, la app funcionará con LocalStorage

## 📄 Licencia

Este proyecto es de uso personal.

## 🤝 Contribuciones

Este es un proyecto personal, pero las sugerencias son bienvenidas.

---

Hecho con ❤️ usando React y Vite

