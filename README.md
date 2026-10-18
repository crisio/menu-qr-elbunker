# El Bunker · Menú QR

Menú digital de **El Bunker · La casa de las carnes**, accesible por código QR.

- **Menú:** https://elbunker.cristopherpineda.com/
- **Editor (desde el celular):** https://elbunker.cristopherpineda.com/admin.html
- **QR para imprimir:** https://elbunker.cristopherpineda.com/qr.html

## Rápido por diseño

- Toda la página es un solo archivo (`index.html`, ~19 KB comprimido, con el logo incluido) más `menu.json` (~5 KB). No usa librerías ni fuentes externas.
- Las fotos se comprimen automáticamente al subirlas (WebP/JPEG, máx. 1400 px) y se crea una miniatura de ~300 px para la lista.
- Las imágenes de la lista cargan solo cuando aparecen en pantalla. Los videos solo se descargan al abrir el plato.
- Optimizado para iPhone y Android: respeta el notch, el botón "atrás" de Android cierra la ficha del plato y los campos no hacen zoom.

## Pedidos por WhatsApp

- Cada plato tiene un botón **+** que lo agrega al pedido con un toque (se pone verde cuando ya está en el pedido). Tocando el plato se abre su ficha con fotos y cantidad. Abajo aparece **Ver mi pedido** con el total.
- Para quitar un plato del pedido: se **desliza a la derecha** (en la lista del menú o en *Tu pedido*), o se abre el plato y se toca **🗑 Quitar del pedido**. Sale un aviso con **Deshacer** por si fue sin querer.
- El botón flotante de WhatsApp viene **apagado** para que pidan con **+** y te llegue la orden completa. Se enciende o apaga en el editor → *Información del restaurante* → *WhatsApp*.
- Si el botón flotante está encendido, se oculta mientras haya algo en el pedido, para que el pedido siempre salga con la orden completa.
- En **Tu pedido** elige **En el local** o **A domicilio**:
  - **En el local:** número de mesa opcional. Si pone la mesa, el nombre es opcional; si no tiene mesa, el nombre es obligatorio (para llamarlo cuando esté listo).
  - **A domicilio:** nombre y dirección obligatorios; si quiere, agrega su ubicación GPS.
- Si el local tiene ubicación guardada, el menú revisa dónde está el cliente: fuera del radio lo marca **A domicilio**, dentro lo marca **En el local**. El cliente puede cambiarlo.
- **Enviar pedido por WhatsApp** abre WhatsApp con todo el pedido escrito: platos, cantidades, total, nombre y entrega.
- **Horario de pedidos:** por ahora vacío, o sea, pedidos a toda hora. Se pone en el editor → *Información del restaurante* → *Horario de pedidos* (hora de Honduras, sin importar la hora del teléfono del cliente). Fuera de ese horario el menú se puede ver, pero no se pueden armar ni enviar pedidos; el pedido que el cliente ya tenía queda guardado para cuando abran.
- Para guardar la ubicación del local: abre el editor **estando en el local** → *Información del restaurante* → **📍 Usar mi ubicación actual** → **Guardar cambios**. El radio (150 m por defecto) se cambia ahí mismo.

## Editar el menú desde el celular

1. Abre **`admin.html`** (link arriba).
2. La primera vez te pide un **token de GitHub** (los pasos aparecen en la pantalla):
   - Ve a https://github.com/settings/personal-access-tokens/new
   - *Repository access* → **Only select repositories** → `menu-qr-elbunker`
   - *Permissions* → **Contents: Read and write**
   - **Generate token**, cópialo y pégalo en el editor. Queda guardado solo en ese teléfono.
3. Toca un plato para editar el nombre, la descripción, el precio, la disponibilidad o el sello "Recomendado". Cada categoría tiene una **nota** opcional que sale bajo el título (por ejemplo, los acompañantes de las parrilladas).
4. Usa **📷 Agregar foto** / **🎬 Agregar video**. Las flechas ◀ ▶ cambian el orden y la primera foto es la que se ve en la lista.
5. Toca **Guardar cambios**. El menú público se actualiza en 1–2 minutos.

### Instalar el editor como app (Windows, Android, iPhone)

- **Windows (Edge o Chrome):** abre `admin.html` y toca **⬇ Instalar app** en la barra verde (o el ícono de instalar en la barra de direcciones). Queda con su ícono en el escritorio y en el menú Inicio.
- **Android (Chrome):** menú ⋮ → **Instalar app**.
- **iPhone (Safari):** botón Compartir → **Agregar a inicio**.

El menú público (`index.html`) también se puede instalar de la misma forma, con su propio ícono.

### Videos

- Clips cortos (10–20 s), máximo 40 MB.
- En iPhone, para que el video también se vea en Android: *Ajustes → Cámara → Formatos → **Más compatible***.

## Estructura

| Archivo | Para qué |
|---|---|
| `index.html` | Menú público |
| `menu.json` | Contenido del menú (lo escribe el editor) |
| `admin.html` | Editor para el celular |
| `qr.html` | Tarjeta con el QR para las mesas: se imprime o se descarga en PNG (1080 × 1440) |
| `logo.svg` | Logo de El Bunker en vector (claro, para fondos oscuros) |
| `media/` | Fotos y videos de los platos |

## Publicar (GitHub Pages + dominio propio)

1. En GitHub: *Settings → Pages → Source: Deploy from a branch* → `main` / `(root)`.
2. En Cloudflare, registro DNS **CNAME** `elbunker` → `crisio.github.io`, con la **nube gris** (*DNS only*).
3. El archivo `CNAME` ya trae `elbunker.cristopherpineda.com`. Cuando GitHub termine de validar el dominio, activa **Enforce HTTPS** en la misma página de Pages.

## Probar localmente

```bash
python3 -m http.server 8000
# abre http://localhost:8000
```
