# Sesiones exploratorias

Cada sesión tiene un objetivo (*charter*), un tiempo fijo y notas de lo que se encontró.

## Sesión 1 · Login y control de acceso · 30 min

**Objetivo:** explorar el login con cada usuario y combinaciones inválidas para encontrar accesos indebidos o mensajes confusos.

- Probé los 6 usuarios, contraseñas con espacios, mayúsculas y campos vacíos.
- Abrí `/inventory.html` sin sesión: la app vuelve al login con el mensaje *You can only access '/inventory.html' when you are logged in*. ✅
- Después del logout, el botón *Atrás* del navegador no vuelve al catálogo. ✅
- Sin hallazgos.

## Sesión 2 · Catálogo con usuarios problemáticos · 45 min

**Objetivo:** comparar el catálogo de cada usuario contra `standard_user`.

- `problem_user`: imágenes repetidas → **BUG-01**; orden por precio roto → **BUG-02**; 3 de 6 productos no se agregan → **BUG-03**.
- `visual_user`: precios distintos en cada carga → **BUG-06**.
- `performance_glitch_user`: el login tarda unos 5 s contra 0,1 s de `standard_user`. Lo anoto como observación, no como bug, porque no hay un requisito de tiempo; si existiera un SLA, sería un bug de severidad media.

## Sesión 3 · Checkout de punta a punta · 45 min

**Objetivo:** completar compras con cada usuario y validar datos, totales y confirmación.

- `standard_user`: subtotal = suma de precios y total = subtotal + impuesto (8%). ✅
- `problem_user`: el apellido pisa el nombre → **BUG-04**.
- `error_user`: Finish no termina la compra → **BUG-05**.
- El código postal acepta letras y símbolos (`ab#$`). Lo anoto como **pregunta para producto**: ¿hay que validar el formato?
