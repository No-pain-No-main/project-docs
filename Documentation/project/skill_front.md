# Code Review Frontend — NoPainNoMain
## Archivos revisados
- `src/main.js` → Capa: Punto entrada
- `src/router/index.js` → Capa: Router
- `src/layouts/AdminLayout.vue` → Capa: Layout
- `src/layouts/StudentLayout.vue` → Capa: Layout
- `src/layouts/AuthLayout.vue` → Capa: Layout
- `src/components/auth/LoginForm.vue` → Capa: Componente UI
- `src/components/auth/RegisterForm.vue` → Capa: Componente UI

---

## 🟡 SHOULD
### `src/router/index.js`
**Sugerencia:** agregar un catch-all `/:pathMatch(.*)*` para manejar rutas 404 y añadir guards de navegación (`beforeEach`, `meta.requiresAuth`) para proteger `/student` y `/admin` según rol/auth.

### `src/components/auth/LoginForm.vue`
**Sugerencia:** cuando se integre backend, delegar la autenticación a un service (por ejemplo `authService.login()`) y mantener la lógica de navegación/ruta fuera del componente de UI.

### `src/components/auth/RegisterForm.vue`
**Sugerencia:** extraer la lógica de registro simulado a un service y evitar mantener esa lógica de negocio en el componente de formulario.

---

## 🟢 PASS
- `src/router/index.js` — usa lazy loading en todas las rutas y mantiene la segregación de grupos `/`, `/student`, `/admin`.
- `src/layouts/AdminLayout.vue` — solo estructura, contiene `<RouterView />`, sin lógica de negocio.
- `src/layouts/StudentLayout.vue` — solo estructura, contiene `<RouterView />`, sin lógica de negocio.
- `src/layouts/AuthLayout.vue` — solo estructura y contiene `<RouterView />`.
- `src/main.js` — configuración correcta de Vue + Pinia + router.

---

## Resumen
| Nivel     | Cantidad |
|-----------|----------|
| 🔴 MUST   | 0        |
| 🟡 SHOULD | 3        |
| 🟢 PASS   | 5        |

**Veredicto:** APROBADO
