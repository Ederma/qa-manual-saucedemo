# Plan de pruebas · SauceDemo

**Versión:** 1.0 · **Autor:** Eder Marroquín · **Fecha:** octubre 2026

## 1. Objetivo

Validar que un cliente pueda iniciar sesión, explorar el catálogo, armar un carrito y completar una compra en [SauceDemo](https://www.saucedemo.com), y detectar defectos antes de que lleguen a producción.

## 2. Alcance

| Incluido | Fuera de alcance |
| --- | --- |
| Login y mensajes de error | Pruebas de carga y rendimiento |
| Catálogo: listado, orden y detalle de producto | Pagos reales (la app no procesa pagos) |
| Carrito: agregar, quitar, contador | Accesibilidad completa (solo chequeos básicos) |
| Checkout: datos, resumen, totales y confirmación | Navegadores móviles |
| Menú lateral: logout y reset del estado | |

## 3. Usuarios de prueba

La app ofrece usuarios con comportamientos distintos; cada uno se prueba como un escenario propio.

| Usuario | Para qué se usa |
| --- | --- |
| `standard_user` | Flujo feliz, línea base de comparación |
| `locked_out_user` | Usuario bloqueado |
| `problem_user` | Defectos funcionales |
| `error_user` | Errores en acciones del flujo |
| `visual_user` | Defectos visuales |
| `performance_glitch_user` | Demoras de respuesta |

## 4. Enfoque

1. **Pruebas exploratorias por sesiones** (ver [exploratorio.md](exploratorio.md)): 30 a 45 minutos con un objetivo concreto por sesión.
2. **Casos de prueba diseñados** con partición de equivalencias y valores límite en los formularios (ver [casos/casos-de-prueba.md](casos/casos-de-prueba.md)).
3. **Comparación contra la línea base:** cada comportamiento de un usuario con problemas se compara con `standard_user`.
4. **Regresión automatizada** de los casos críticos en [playwright-ai-e2e](https://github.com/Ederma/playwright-ai-e2e).

## 5. Criterios

- **Entrada:** la app responde y los usuarios de prueba pueden iniciar sesión.
- **Salida:** 100% de los casos críticos ejecutados, ningún bug crítico abierto sin reportar, evidencia adjunta en cada bug.
- **Severidad:** *Crítica* bloquea la compra · *Alta* da un resultado incorrecto sin bloquear · *Media* confunde al usuario · *Baja* es cosmética.

## 6. Entorno

Chrome 1xx en macOS, resolución 1280×900. Sitio público, sin datos reales.

## 7. Resultado

| Métrica | Valor |
| --- | --- |
| Casos ejecutados | 24 |
| Pasaron | 18 |
| Fallaron | 6 |
| Bugs reportados | 6 (2 críticos, 3 altos, 1 medio) |

Detalle de cada bug en [bugs/](bugs/).
