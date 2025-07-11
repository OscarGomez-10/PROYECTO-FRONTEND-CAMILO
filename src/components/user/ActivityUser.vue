<template>
    <div class="container py-4">
        <!-- Historial de Actividades -->
        <div class="activity-container p-4 rounded-4 shadow mb-4">
            <h5 class="fw-bold text-white mb-4">
                <i class="bi bi-journal-text text-warning me-2"></i>
                Historial de Actividades
            </h5>

            <div v-for="(actividad, i) in actividades" :key="i"
                class="activity-card d-flex justify-content-between align-items-center p-3 rounded-4 mb-3">
                <div class="d-flex align-items-center">
                    <div class="icon-circle me-3" :class="actividad.bgColor">
                        <i :class="actividad.icono" class="fs-4 text-white"></i>
                    </div>
                    <div>
                        <div class="fw-semibold text-white">{{ actividad.nombre }}</div>
                        <small class="text-light">{{ actividad.tiempo }}</small>
                    </div>
                </div>
                <span class="badge-points" :class="actividad.puntos < 0 ? 'bg-danger' : 'bg-warning'">
                    {{ actividad.puntos > 0 ? '+' : '' }}{{ actividad.puntos }} pts
                </span>
            </div>
        </div>

        <!-- Estadísticas + Logros -->
        <div class="row g-3">
            <!-- Estadísticas Semanales -->
            <div class="col-md-6">
                <div class="card-glass p-4 rounded-4 h-100">
                    <h5 class="fw-bold text-white mb-4">
                        <i class="bi bi-bar-chart-line-fill me-2 text-info"></i>
                        Estadísticas Semanales
                    </h5>
                    <div class="d-flex justify-content-around text-center">
                        <div>
                            <h3 class="text-success fw-bold">28</h3>
                            <p class="text-light">Pausas Realizadas</p>
                        </div>
                        <div>
                            <h3 class="text-info fw-bold">140</h3>
                            <p class="text-light">Puntos Ganados</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Logros -->
            <div class="col-md-6">
                <div class="card-glass p-4 rounded-4 h-100">
                    <h5 class="fw-bold text-white mb-4">
                        <i class="bi bi-trophy-fill text-warning me-2"></i>
                        Logros
                    </h5>
                    <ul class="list-unstyled">
                        <li class="d-flex align-items-center mb-3">
                            <i class="bi bi-fire text-danger me-3 fs-4"></i>
                            <span class="text-light">Racha de 5 días</span>
                        </li>
                        <li class="d-flex align-items-center mb-3">
                            <i class="bi bi-star-fill text-warning me-3 fs-4"></i>
                            <span class="text-light">100 pausas completadas</span>
                        </li>
                        <li class="d-flex align-items-center">
                            <i class="bi bi-person-arms-up text-success me-3 fs-4"></i>
                            <span class="text-light">Atleta de la semana</span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const actividades = [
    {
        nombre: "Estiramiento de Cuello",
        tiempo: "Hace 30 minutos",
        puntos: 5,
        bgColor: "bg-success",
        icono: "bi bi-arrow-up-right", // Icono alternativo
    },
    {
        nombre: "Caminata Corta",
        tiempo: "Hace 1 hora",
        puntos: 10,
        bgColor: "bg-primary",
        icono: "bi bi-person-walking",
    },
    {
        nombre: "Respiración Profunda",
        tiempo: "Hace 2 horas",
        puntos: 5,
        bgColor: "bg-info",
        icono: "bi bi-cloud", // Icono alternativo
    },
    {
        nombre: "Café Gratis Canjeado",
        tiempo: "Ayer",
        puntos: -50,
        bgColor: "bg-danger",
        icono: "bi bi-cup-hot",
    },
];
</script>

<style scoped>
.activity-container {
    background: linear-gradient(135deg, #1e3a8a, #3b82f6);
    border-radius: 1.5rem;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
}

.card-glass {
    background: linear-gradient(135deg, #1e3a8a, #3b82f6);
    backdrop-filter: blur(8px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.25);
}

.activity-card {
    background-color: rgba(255, 255, 255, 0.07);
    border: 1px solid rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(4px);
    transition: all 0.3s ease;
}

.activity-card:hover {
    transform: translateY(-2px);
    background-color: rgba(255, 255, 255, 0.12);
}

.icon-circle {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.badge-points {
    color: white;
    padding: 6px 14px;
    border-radius: 20px;
    font-weight: 600;
    font-size: 0.9rem;
    min-width: 80px;
    text-align: center;
}
</style>
