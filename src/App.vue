<script setup>
import { ref } from 'vue';
import { Collapse } from 'bootstrap';

// Componentes de usuario
import ActivityUser from './components/user/ActivityUser.vue';
import DashboardUser from './components/user/DashboardUser.vue';
import HealthUser from './components/user/HealthUser.vue';
import RecommendationsUser from './components/user/RecommendationsUser.vue';
import RewardsUser from './components/user/RewardsUser.vue';

// Componentes de admin
import UsuarioAdmin from "./components/admin/usuarioAdmin.vue";
import DashboardAdmin from "./components/admin/dashboardAdmin.vue";
import AccionesAdmin from "./components/admin/accionesAdmin.vue";
import ReportesAdmin from "./components/admin/reportesAdmin.vue";
import ConfiguracionAdmin from "./components/admin/configuracionAdmin.vue";

// Estado de la aplicación
const currentView = ref("dashboard");
const isAdmin = ref(true);
const navbarCollapse = ref(null);

const toggleUserType = () => {
  isAdmin.value = !isAdmin.value;
  currentView.value = "dashboard";
  closeNavbar();
};

const closeNavbar = () => {
  if (navbarCollapse.value) {
    const bsCollapse = Collapse.getInstance(navbarCollapse.value) ||
      new Collapse(navbarCollapse.value, { toggle: false });
    bsCollapse.hide();
  }
};

const changeView = (view) => {
  currentView.value = view;
  closeNavbar();
};
</script>

<template>
  <div class="d-flex flex-column vh-100">
    <!-- ========== NAVBAR SUPERIOR AZUL ========== -->
    <nav class="navbar navbar-expand-lg bg-primary p-2 shadow-sm sticky-top">
      <div class="container-fluid">
        <!-- Logo y marca -->
        <div class="d-flex align-items-center">
          <span class="trophy fs-4 me-2 text-white">🏆</span>
          <span class="navbar-brand text-white fw-bold mb-0">HR Gamification</span>
        </div>

        <!-- Botón toggle para móviles -->
        <button class="navbar-toggler border-0" type="button" data-bs-toggle="collapse" data-bs-target="#mainNavbar"
          aria-controls="mainNavbar">
          <i class="bi bi-list text-white fs-3"></i>
        </button>

        <!-- Contenido del navbar -->
        <div class="collapse navbar-collapse" id="mainNavbar" ref="navbarCollapse">
          <!-- Menú principal -->
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <!-- Menú Admin -->
            <template v-if="isAdmin">
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'dashboard' }"
                  @click="changeView('dashboard')">
                  <i class="bi bi-house me-1"></i> Dashboard
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'empleados' }"
                  @click="changeView('empleados')">
                  <i class="bi bi-people me-1"></i> Empleados
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'acciones' }"
                  @click="changeView('acciones')">
                  <i class="bi bi-bullseye me-1"></i> Acciones
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'reportes' }"
                  @click="changeView('reportes')">
                  <i class="bi bi-bar-chart me-1"></i> Reportes
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'configuracion' }"
                  @click="changeView('configuracion')">
                  <i class="bi bi-gear me-1"></i> Configuración
                </button>
              </li>
            </template>

            <!-- Menú Usuario -->
            <template v-else>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'dashboard' }"
                  @click="changeView('dashboard')">
                  <i class="bi bi-house me-1"></i> Dashboard
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'actividad' }"
                  @click="changeView('actividad')">
                  <i class="bi bi-activity me-1"></i> Actividad
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'salud' }"
                  @click="changeView('salud')">
                  <i class="bi bi-heart-pulse me-1"></i> Salud
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'recompensas' }"
                  @click="changeView('recompensas')">
                  <i class="bi bi-award me-1"></i> Recompensas
                </button>
              </li>
              <li class="nav-item">
                <button class="btn btn-pine mx-1 my-1" :class="{ 'active': currentView === 'recomendaciones' }"
                  @click="changeView('recomendaciones')">
                  <i class="bi bi-lightbulb me-1"></i> Recomendaciones
                </button>
              </li>
            </template>
          </ul>

          <!-- Controles del usuario -->
          <div class="d-flex align-items-center ms-auto">
            <!-- Botón cambiar modo -->
            <button @click="toggleUserType" class="btn btn-pine me-3">
              <i class="bi bi-arrow-repeat me-1"></i>
              {{ isAdmin ? 'Modo Usuario' : 'Modo Admin' }}
            </button>

            <!-- Perfil de usuario -->
            <div class="dropdown">
              <button class="btn btn-pine dropdown-toggle d-flex align-items-center gap-2 text-white" type="button"
                id="userDropdown" data-bs-toggle="dropdown">
                <div
                  class="rounded-circle bg-white text-primary d-flex align-items-center justify-content-center fw-bold"
                  style="width: 32px; height: 32px;">
                  {{ isAdmin ? 'AD' : 'US' }}
                </div>
                <span class="d-none d-md-inline fw-semibold">{{ isAdmin ? 'Administrador' : 'Usuario' }}</span>
              </button>
              <ul class="dropdown-menu dropdown-menu-end">
                <li><a class="dropdown-item" href="#"><i class="bi bi-person me-2"></i>Perfil</a></li>
                <li><a class="dropdown-item" href="#"><i class="bi bi-gear me-2"></i>Configuración</a></li>
                <li>
                  <hr class="dropdown-divider">
                </li>
                <li><a class="dropdown-item text-danger" href="#"><i class="bi bi-box-arrow-right me-2"></i>Cerrar
                    sesión</a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <!-- ========== CONTENIDO PRINCIPAL ========== -->
    <main class="flex-grow-1 overflow-auto bg-light p-3">
      <!-- Vistas de Admin -->
      <template v-if="isAdmin">
        <DashboardAdmin v-if="currentView === 'dashboard'" class="animate__animated animate__fadeIn" />
        <UsuarioAdmin v-if="currentView === 'empleados'" class="animate__animated animate__fadeIn" />
        <AccionesAdmin v-if="currentView === 'acciones'" class="animate__animated animate__fadeIn" />
        <ReportesAdmin v-if="currentView === 'reportes'" class="animate__animated animate__fadeIn" />
        <ConfiguracionAdmin v-if="currentView === 'configuracion'" class="animate__animated animate__fadeIn" />
      </template>

      <!-- Vistas de Usuario -->
      <template v-else>
        <DashboardUser v-if="currentView === 'dashboard'" class="animate__animated animate__fadeIn" />
        <ActivityUser v-if="currentView === 'actividad'" class="animate__animated animate__fadeIn" />
        <HealthUser v-if="currentView === 'salud'" class="animate__animated animate__fadeIn" />
        <RewardsUser v-if="currentView === 'recompensas'" class="animate__animated animate__fadeIn" />
        <RecommendationsUser v-if="currentView === 'recomendaciones'" class="animate__animated animate__fadeIn" />
      </template>
    </main>
  </div>
</template>

<style scoped>
* {
  color: black !important;
}

/* ========== ESTILOS PERSONALIZADOS ========== */
/* Fondo azul para el navbar */
.bg-primary {
  background-color: #0d6efd !important;
}

/* Botones verde pino */
.btn-pine {
  background-color: white;
  /* Verde pino */
  color: white;
  border: none;
  border-radius: 6px;
  padding: 8px 16px;
  transition: all 0.3s ease;
}

/* Efecto hover más claro */
.btn-pine:hover {
  background-color: #ecf9f9 !important;
  /* Verde pino claro */
  color: white;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Estado activo */


/* Mejoras para el navbar */
.navbar {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
  min-height: 100px;
}

/* Efecto hover para items del dropdown */
.dropdown-item:hover {
  background-color: #f8f9fa;
}

/* Animaciones para las vistas */
.animate__animated {
  --animate-duration: 0.3s;
}

/* Ajustes para el contenido principal */
main {
  background-color: #f8f9fa;
  min-height: calc(100vh - 56px);
  /* Ajusta según altura del navbar */
}

/* Iconos alineados verticalmente */
.bi {
  vertical-align: middle;
}

/* Toggle personalizado para móviles */
.navbar-toggler:focus {
  box-shadow: none;
}
</style>
