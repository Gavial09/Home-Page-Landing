# Laboratory Activity 5: Developing Front End and Consuming Restful API (By Group)

## <ins> The Project </ins>
The task is to build a small `Vue` app step-by-step:

Clean project → UI → pages → Pinia auth state → Navbar/Logout → router guards → public login via DummyJSON → token interceptor → protected fetch.

### <ins> Milestone 0 — Create a clean Vue 3 project </ins>
Goal: A fresh `Vite + Vue 3` app running locally.

Verify: Vite starter at `http://localhost:5173`.

### <ins> Milestone 1 — Add Bootstrap and a simple layout shell </ins>
Goal: Install `Bootstrap`; add container + navbar placeholder.

**src/main.js** (minimal)

**src/App.vue** (temp layout)

### <ins> Milestone 2 — Add Vue Router and three pages (no guards yet) </ins>
Goal: Create Home, Login, Dashboard. Navigation works; all public.

**src/pages/HomePage.vue**

**src/pages/LoginPage.vue** (UI only)

**src/pages/DashboardPage.vue**

**src/router/index.js**

**src/main.js:** register router; update **App.vue** with `<RouterLink>` nav.

### <ins> Milestone 3 — Introduce Pinia (state only) </ins>
Goal: Auth store persisting token/user to `localStorage`.

**src/stores/auth.js** 

**src/main.js** (register Pinia)

### <ins> Milestone 4 — Navbar auth state + Logout </ins>
Goal: Navbar shows Login/Logout; implement `Logout`.

**src/components/AppNavbar.vue**

### <ins> Milestone 5 — Protect routes with navigation guards </ins>
Goal: Make Dashboard protected; redirect guests; block Login for logged-in users.

**src/router/index.js**

### <ins> Milestone 6 — Axios client + DummyJSON Login </ins>
Goal: Use `Axios` to call the public DummyJSON login, then store token+user.

**src/api/http.js**

**src/pages/LoginPage.vue** (call DummyJSON)

### <ins> Milestone 7 — Axios interceptors (attach token; auto-logout on 401) </ins>
Goal: Auto-attach `Authorization: Bearer <token>`; clear auth on 401.

**src/api/http.js** (enhanced)

### <ins> Milestone 8 — Protected fetch on Dashboard (verify token) </ins>
Goal: After login, call `/auth/me` and render user info.

**src/pages/DashboardPage.vue**

# <ins> Run Steps </ins>
Visit `http://localhost:5173`

Login with following credentials:

Username: `emilys`

Password: `emilyspass`

Open `DevTools` on browser using `F12`
