# VCM2
Un album de recuerdos

## Cómo ejecutar
1. Desde la raíz del repositorio (`/workspace/VCM2`), levanta un servidor estático.
   - Opción Python: `python3 -m http.server 8000`
   - Opción VSCode: Live Server apuntando a la raíz del repo.
2. Abre la app en el navegador con `http://localhost:8000/index.html` (ajusta el puerto si usas otro).
3. **No uses `file://` ni abras `index.html` con doble clic**, porque las peticiones a recursos como `https://raw.githubusercontent.com/nvkelso/natural-earth-vector/master/geojson/ne_10m_admin_1_states_provinces.geojson` pueden fallar por políticas del navegador.
4. Verifica en DevTools > Network que `https://raw.githubusercontent.com/nvkelso/natural-earth-vector/master/geojson/ne_10m_admin_1_states_provinces.geojson` responde `200`.

## Guardado persistente con Firebase (multi-dispositivo)
La app ahora guarda siempre en `localStorage` y, si completas Firebase, también sincroniza en Firestore para que los datos aparezcan al abrir en otro dispositivo.

1. Abre `index.html` y completa `FIREBASE_CONFIG` con tu proyecto de Firebase.
2. En Firestore, crea la base en modo de pruebas (o reglas propias) y usa la colección `albumes`.
3. Comparte la URL incluyendo el query param `album`, por ejemplo:
   - `http://localhost:8000/index.html?album=nuestro-viaje`
4. Si dos dispositivos abren el mismo `album`, comparten el mismo contenido.

> Nota: si `FIREBASE_CONFIG` está vacío, la app funciona en modo solo local (persistencia en el navegador actual).
