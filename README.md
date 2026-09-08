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
