# Casos de prueba · SauceDemo

24 casos ejecutados en octubre 2026. También disponibles en [casos-de-prueba.csv](casos-de-prueba.csv) para importar en Jira, TestRail o una planilla.

| ID | Módulo | Caso | Usuario | Pasos | Resultado esperado | Resultado | Bug |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-01 | Login | Login correcto | `standard_user` | Ingresar usuario y contraseña válidos; clic en Login | Entra al catálogo (Products) | ✅ Pasó |  |
| TC-02 | Login | Usuario bloqueado | `locked_out_user` | Ingresar credenciales; clic en Login | Mensaje: Sorry, this user has been locked out. | ✅ Pasó |  |
| TC-03 | Login | Contraseña incorrecta | `standard_user` | Ingresar usuario válido y contraseña incorrecta | Mensaje: Username and password do not match | ✅ Pasó |  |
| TC-04 | Login | Campos vacíos | `—` | Clic en Login sin completar | Mensaje: Username is required | ✅ Pasó |  |
| TC-05 | Login | Contraseña vacía | `standard_user` | Completar solo el usuario | Mensaje: Password is required | ✅ Pasó |  |
| TC-06 | Login | Acceso directo sin sesión | `—` | Abrir /inventory.html sin haber iniciado sesión | Vuelve al login con un mensaje de acceso restringido | ✅ Pasó |  |
| TC-07 | Catálogo | Se listan 6 productos con imagen propia | `standard_user` | Entrar al catálogo | 6 productos, cada uno con su imagen | ✅ Pasó |  |
| TC-08 | Catálogo | Imágenes por producto | `problem_user` | Entrar al catálogo | Cada producto con su imagen | ❌ Falló | [BUG-01](../bugs/BUG-01.md) |
| TC-09 | Catálogo | Orden Z→A | `standard_user` | Elegir Name (Z to A) | Productos ordenados de Z a A | ✅ Pasó |  |
| TC-10 | Catálogo | Orden por precio menor a mayor | `standard_user` | Elegir Price (low to high) | Precios ascendentes | ✅ Pasó |  |
| TC-11 | Catálogo | Orden por precio menor a mayor | `problem_user` | Elegir Price (low to high) | Precios ascendentes | ❌ Falló | [BUG-02](../bugs/BUG-02.md) |
| TC-12 | Catálogo | Precios correctos | `visual_user` | Comparar los precios con los de standard_user | Mismos precios | ❌ Falló | [BUG-06](../bugs/BUG-06.md) |
| TC-13 | Carrito | Agregar dos productos | `standard_user` | Agregar Backpack y Bike Light | Contador en 2 | ✅ Pasó |  |
| TC-14 | Carrito | Quitar un producto | `standard_user` | Agregar 2 y quitar 1 | Contador en 1 | ✅ Pasó |  |
| TC-15 | Carrito | Agregar cualquier producto | `problem_user` | Agregar Bolt T-Shirt | Contador en 1 | ❌ Falló | [BUG-03](../bugs/BUG-03.md) |
| TC-16 | Carrito | El carrito se mantiene al navegar | `standard_user` | Agregar un producto, abrir su detalle y volver | El producto sigue en el carrito | ✅ Pasó |  |
| TC-17 | Checkout | Datos obligatorios: nombre | `standard_user` | Continuar sin First Name | Mensaje: First Name is required | ✅ Pasó |  |
| TC-18 | Checkout | Datos obligatorios: código postal | `standard_user` | Continuar sin código postal | Mensaje: Postal Code is required | ✅ Pasó |  |
| TC-19 | Checkout | Nombre y apellido se guardan | `problem_user` | Escribir Eder y Marroquin | Cada valor en su campo | ❌ Falló | [BUG-04](../bugs/BUG-04.md) |
| TC-20 | Checkout | Subtotal = suma de precios | `standard_user` | Llevar 2 productos al resumen | Item total = suma de los precios | ✅ Pasó |  |
| TC-21 | Checkout | Total = subtotal + impuesto | `standard_user` | Ver el resumen | Total = Item total + Tax | ✅ Pasó |  |
| TC-22 | Checkout | Compra completa | `standard_user` | Clic en Finish | Mensaje: Thank you for your order! | ✅ Pasó |  |
| TC-23 | Checkout | Compra completa | `error_user` | Clic en Finish | Mensaje: Thank you for your order! | ❌ Falló | [BUG-05](../bugs/BUG-05.md) |
| TC-24 | Menú | Logout | `standard_user` | Menú → Logout | Vuelve al login y no se puede volver atrás al catálogo | ✅ Pasó |  |
