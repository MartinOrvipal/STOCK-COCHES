# 🗺️ Mapa de Stock de Coches  
**Leaflet + Google Sheets (CSV)**

Proyecto web que muestra un **mapa interactivo de España** con el **stock de coches por ciudad/provincia**, usando datos en tiempo real desde **Google Sheets** y visualización con **Leaflet**.

---

## 📌 ¿Qué hace este proyecto?

Este HTML pinta un mapa de España (Leaflet + OpenStreetMap) y encima añade:

### 🚗 1. Etiquetas de stock en el mapa
- Se leen desde una **Google Sheet publicada como CSV** (`gid=0`).
- Cada fila representa una etiqueta con:
  - Ciudad
  - Marca
  - Stock
  - Logo
  - Latitud
  - Longitud
- **No hay pines azules**: se usan **tooltips permanentes** con diseño tipo tarjeta.

### 🚛 2. Tarjetas de camiones
- Se leen desde otra hoja CSV (`gid=614991280`).
- Aparecen como tarjetas en la esquina inferior izquierda.
- Cada provincia muestra icono, nombre y número de camiones.
- **CARGAS AGENCIA** se muestra como tarjeta especial arriba a la izquierda.

### 📺 3. Compatibilidad TV Bro
- Detecta el navegador TV Bro por `userAgent`.
- Aplica la clase `tvbro` al `<body>`.
- Reduce tamaños para verse correctamente en TV.

### 🔄 4. Actualización automática
- Recarga automática cada **5 minutos**.

---

## 🧱 Estructura del proyecto

```
/assets
  camion-murcia.png
  camion-val-pal.png
  cargas-agencia.png
index.html
README.md
```

---

## 🎨 Colores por ciudad / provincia

Cada ciudad tiene una clase CSS propia:

```css
.bg-valencia { background-color: #38761d; }
.bg-madrid   { background-color: #f1c232; }
.bg-lisboa   { background-color: #a64d79; }
.bg-default  { background-color: #999999; }
```

---

## ➕ Añadir una nueva ciudad con color

### 1. CSS
```css
.bg-sevilla { background-color: #123456; }
```

### 2. JavaScript
```js
case 'sevilla': bgClass = 'bg-sevilla'; break;
```

⚠️ Usar nombres sin tildes ni caracteres especiales.

---

## 📊 Añadir nueva etiqueta de stock

En la Google Sheet (`gid=0`) añadir:
- CIUDAD
- MARCA
- STOCK
- LOGO
- LATITUD
- LONGITUD

---

## 🚚 Añadir nueva tarjeta de camiones

En la hoja (`gid=614991280`) añadir:
- PROVINCIA
- Nº CAMIONES

Icono requerido en `/assets`:
```
camion-<provincia>.png
```

---

## 🚨 CARGAS AGENCIA

Si PROVINCIA = CARGAS AGENCIA:
- Tarjeta superior izquierda
- Icono: `assets/cargas-agencia.png`

---

## 🛠️ Cambios rápidos

### Zoom / centro
```js
mapa.setView([40.5, -3.5], 6.2);
```

### Auto-recarga
```js
setTimeout(() => location.reload(), 300000);
```

---

## ✅ Checklist si algo no se ve
- Latitud y longitud válidas
- CSV publicado
- Icono existente
- Ciudad configurada en el switch
