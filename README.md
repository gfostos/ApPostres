# Costos de Postres

Web instalable (PWA) para registrar ingredientes y empaque, comparar precios entre tiendas, calcular el costo de las recetas y el precio de venta de cada torta.

## Contenido
- `index.html`: la app completa (sin dependencias ni internet)
- `manifest.json`, `sw.js`, `icons/`: permiten instalarla en el celular y usarla sin conexión

## Publicarla (una sola vez, gratis)
Para que se pueda **instalar** en el celular debe estar en una dirección https. Opciones:

1. **Netlify Drop**: entra a app.netlify.com/drop y arrastra la carpeta `costos-postres`. Te da un enlace.
2. **GitHub Pages**: sube la carpeta a un repositorio y activa Pages en Settings → Pages.

Luego, en el celular de tu mamá, abre el enlace en Chrome → menú ⋮ → **Instalar app** (en iPhone: Safari → Compartir → **Agregar a inicio**).

Si ya la habías publicado, sube los archivos nuevos encima: los datos guardados en el celular se conservan y se convierten solos al abrir la app.

## Dónde se guardan los datos
En el navegador del celular donde se usa (no se envían a ningún servidor).
Para respaldarlos: **Más → Guardar copia** y elegir **Drive** en el menú de compartir.
Para verlos en otro dispositivo: guardar la copia en un dispositivo y usar **Más → Restaurar copia** en el otro.

> Importante: si se borran los datos del navegador, se pierden. Por eso la app avisa cuando pasan 7 días sin copia.

## Ingredientes y tiendas
Cada ingrediente (Huevos, Harina…) aparece **una sola vez** y guarda un precio por cada tienda donde se compra: Pasadena, Aramar, D1, ARA, Roma Distribuciones, Belen Salsamentaria, o cualquier otra con "➕ Añadir otra tienda".

- La tienda **más barata** sale primero, en verde, con ✓ Más barato.
- Las demás muestran cuánto más caras son (por ejemplo "+33% más caro"). La comparación se hace por precio por unidad, así que sirve aunque los paquetes sean de distinto tamaño.
- Para agregar el precio de otra tienda: abre el ingrediente y toca "+ Agregar precio de otra tienda". Si se crea un ingrediente con un nombre que ya existe, el precio se suma al que ya está.
- **Las recetas usan siempre el precio de la tienda más barata.**
- Al marcar "📦 Es empaque" (cajas, bases, bolsas), el ingrediente se cuenta como empaque en el cálculo del precio.

## Cómo calcula el precio
La receta muestra dos precios de la torta completa, lado a lado (y el valor por porción de cada uno).

**⚡ Precio rápido** (el método de siempre)
1. (Ingredientes + empaque) + 10% de gastos adicionales
2. × 2, redondeado hacia arriba

**⭐ Precio por tiempo** (se calcula cuando se anotan las horas que toma la torta)
1. Ingredientes + 5% de merma (lo que se desperdicia)
2. + Empaque
3. + 10% de gastos adicionales (gas, luz, transporte…)
4. + Tu tiempo: horas × valor de la hora ($8.500 por defecto)
5. = Lo que te cuesta
6. + 30% de ganancia, redondeado hacia arriba

También se muestra el **precio mínimo**: lo que cubre todos los costos sin ganar nada.
Si el precio rápido queda por debajo del precio por tiempo, la app lo avisa.

El 10%, el ×2, la merma y la ganancia son fijos. El valor de la hora y el redondeo se cambian en **Más → Precio de venta**. Las horas se escriben con decimales: 2,5 es dos horas y media.
