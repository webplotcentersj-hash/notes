# 🚀 Guía de Despliegue en Vercel

Esta guía te ayudará a desplegar Ale Notes en Vercel paso a paso.

## 📋 Requisitos Previos

- Una cuenta en [Vercel](https://vercel.com)
- (Opcional) Un proyecto en [Supabase](https://supabase.com) si quieres sincronización en la nube
- Tu código en un repositorio Git (GitHub, GitLab, o Bitbucket)

## 🎯 Pasos para Desplegar

### Paso 1: Preparar el Repositorio

1. Asegúrate de que todos los archivos estén commitados:
   ```bash
   git add .
   git commit -m "Preparado para Vercel"
   git push
   ```

### Paso 2: Conectar con Vercel

#### Método A: Desde la Web (Recomendado)

1. Ve a [vercel.com](https://vercel.com) e inicia sesión
2. Haz clic en **"Add New Project"** o **"Import Project"**
3. Conecta tu cuenta de GitHub/GitLab/Bitbucket si aún no lo has hecho
4. Selecciona el repositorio que contiene Ale Notes
5. Vercel detectará automáticamente que es un proyecto Vite

#### Método B: Desde CLI

```bash
# Instalar Vercel CLI
npm i -g vercel

# Iniciar sesión
vercel login

# Desplegar (primera vez)
vercel

# Para producción
vercel --prod
```

### Paso 3: Configurar Variables de Entorno

**IMPORTANTE:** Si vas a usar Supabase, configura estas variables:

1. En el dashboard de Vercel, ve a tu proyecto
2. Ve a **Settings** > **Environment Variables**
3. Agrega las siguientes variables:

| Variable | Valor | Entornos |
|----------|-------|----------|
| `VITE_SUPABASE_URL` | `https://tu-proyecto.supabase.co` | Production, Preview, Development |
| `VITE_SUPABASE_ANON_KEY` | `tu_clave_anonima` | Production, Preview, Development |

4. Haz clic en **Save**

**Nota:** Si no configuras estas variables, la app funcionará con LocalStorage (solo local, sin sincronización).

### Paso 4: Configurar Supabase (Opcional pero Recomendado)

1. Ve a tu proyecto en Supabase
2. Abre el **SQL Editor**
3. Copia y ejecuta el contenido de `supabase-setup.sql`
4. Verifica que las tablas se hayan creado correctamente

### Paso 5: Desplegar

1. Si usaste el método web, Vercel desplegará automáticamente
2. Si usaste CLI, ejecuta `vercel --prod`
3. Espera a que termine el build (generalmente 1-2 minutos)
4. ¡Listo! Tu app estará disponible en `tu-proyecto.vercel.app`

## 🔄 Actualizaciones Futuras

Cada vez que hagas `git push` a la rama principal:
- Vercel detectará los cambios automáticamente
- Construirá una nueva versión
- La desplegará automáticamente

Para previews de otras ramas:
- Vercel crea automáticamente un preview para cada Pull Request
- Puedes probar cambios antes de hacer merge

## 🐛 Solución de Problemas

### Error: "Build failed"

- Verifica que todas las dependencias estén en `package.json`
- Revisa los logs de build en Vercel para ver el error específico
- Asegúrate de que Node.js versión sea compatible (Vercel usa Node 18+ por defecto)

### Variables de entorno no funcionan

- Verifica que las variables empiecen con `VITE_`
- Asegúrate de que estén configuradas para el entorno correcto (Production)
- Despliega nuevamente después de agregar variables

### La app funciona pero no se conecta a Supabase

- Verifica que las variables de entorno estén correctamente configuradas
- Revisa la consola del navegador para errores
- Asegúrate de que ejecutaste el script SQL en Supabase
- Verifica que las políticas RLS en Supabase permitan acceso

### Rutas no funcionan (404 en rutas directas)

- El archivo `vercel.json` ya está configurado para manejar esto
- Si persiste, verifica que el archivo `vercel.json` esté en la raíz del proyecto

## 📊 Monitoreo

Vercel proporciona:
- **Analytics:** Estadísticas de uso (requiere plan Pro)
- **Logs:** Logs en tiempo real de tu aplicación
- **Deployments:** Historial de todos los despliegues

## 🔒 Seguridad

- ✅ Las variables de entorno están encriptadas en Vercel
- ✅ Solo tú puedes ver las variables de entorno
- ✅ Las builds se ejecutan en un entorno aislado
- ⚠️ No compartas tus claves de Supabase públicamente

## 💡 Tips

- Usa **Preview Deployments** para probar cambios antes de producción
- Configura **Custom Domains** si tienes tu propio dominio
- Activa **Automatic HTTPS** (ya está activado por defecto)
- Revisa los **Build Logs** si algo falla

## 📞 Soporte

- [Documentación de Vercel](https://vercel.com/docs)
- [Documentación de Vite](https://vitejs.dev)
- [Documentación de Supabase](https://supabase.com/docs)

---

¡Feliz despliegue! 🎉


