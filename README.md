# Punto de venta — Cafetería

Punto de venta (POS) simple para una cafetería: catálogo de productos con modificadores (tipo de leche, jarabes, sabores), carrito, cobro, nombre del cliente, tickets e impresión de orden para la barra, y reportes de ventas del día.

Es una sola página web (HTML + CSS + JavaScript), sin dependencias ni instalación. Los datos (productos, ventas, configuración) se guardan en el propio navegador usando `localStorage`.

## Cómo usarlo

### Opción 1: abrir el archivo directamente
1. Descarga este repositorio (botón verde "Code" → "Download ZIP", o `git clone`).
2. Haz doble clic en `index.html`. Se abre en tu navegador y ya puedes usarlo.

### Opción 2: publicarlo en línea con GitHub Pages (para usarlo desde cualquier dispositivo con internet, e instalarlo como app)
1. Sube este repositorio a tu cuenta de GitHub.
2. Ve a **Settings → Pages** en el repositorio.
3. En "Source", selecciona la rama `main` y la carpeta `/ (root)`.
4. Guarda. En un par de minutos tu punto de venta estará disponible en una URL tipo `https://tu-usuario.github.io/nombre-del-repo/`.
5. Abre esa URL en Chrome/Edge (computadora o celular) y busca la opción **"Instalar app"** (ícono de instalación en la barra de direcciones, o "Agregar a pantalla de inicio" en celular). Con esto queda con su propio ícono, se abre en su propia ventana, y sigue funcionando aunque no tengas internet en ese momento.

> Nota: la instalación como app (PWA) y el funcionamiento sin internet solo aplican cuando lo abres desde la URL de GitHub Pages (https). Si abres el archivo `index.html` directamente desde tu computadora (doble clic), funciona igual de bien pero sin esa opción de "Instalar".

> Nota: como los datos se guardan con `localStorage`, cada navegador/dispositivo donde lo abras tendrá su propia información por separado (no se sincroniza automáticamente entre computadora y celular, por ejemplo). Usa el botón "Respaldo de datos" dentro de la pestaña Productos para copiar y restaurar tu información cuando lo necesites.

## Funciones

- Catálogo de productos por categoría, con precio y control de inventario.
- Modificadores por producto (ej. tipo de leche, jarabe, sabor) con costo extra opcional.
- Carrito con nombre de cliente opcional.
- Impresión de ticket para el cliente y de orden/comanda para preparar la bebida.
- Reportes de ventas del día, historial reciente y botón para reiniciar reportes.
- Respaldo manual de datos (exportar/restaurar como texto).

## Próximos pasos

Este proyecto empezó como una versión de navegador antes de convertirlo en una app de escritorio instalable (por ejemplo con Electron o Tauri).

## Sincronizar entre varios dispositivos (opcional)

Por defecto, cada dispositivo guarda sus propios datos por separado. Si quieres que los cambios en un dispositivo (agregar un producto, hacer una venta) se reflejen automáticamente en los demás, puedes conectar una base de datos gratuita de Firebase:

1. Ve a [console.firebase.google.com](https://console.firebase.google.com) e inicia sesión con una cuenta de Google.
2. Da clic en "Crear un proyecto", ponle un nombre y termina el asistente (puedes desactivar Google Analytics, no es necesario).
3. Dentro del proyecto, da clic en el ícono web `</>` para "Agregar app". Ponle un apodo y da clic en "Registrar app" (no necesitas configurar Hosting).
4. Firebase te mostrará un bloque de código con `const firebaseConfig = { ... }`. Copia ese bloque completo.
5. En el menú lateral, ve a "Firestore Database" → "Crear base de datos". Elige "Iniciar en modo de prueba" y selecciona la región más cercana a ti.
6. Dentro de la pestaña "Reglas" de Firestore, reemplaza el contenido por esto y publica:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /posData/{docId} {
         allow read, write: if true;
       }
     }
   }
   ```
7. En tu punto de venta, entra como administrador, ve a **Productos → Sincronización en la nube**, pega el bloque `firebaseConfig` que copiaste, y da clic en "Conectar".
8. Repite el paso 7 en cada dispositivo donde quieras usar el punto de venta, pegando la misma configuración.

> Nota de seguridad: con estas reglas, cualquier persona que tenga esa configuración podría leer o modificar tus datos. Es aceptable para un negocio pequeño con gente de confianza, pero evita compartir públicamente ese bloque de configuración.
