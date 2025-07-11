<template>
    <div class="recommendations-container">
        <!-- Tarjeta de alerta principal -->
        <div class="card recommendation-card mb-4 shadow-sm">
            <div class="card-body text-center">
                <h2 class="h4 mb-3">
                    <i class="bi bi-exclamation-triangle-fill text-warning me-2"></i>
                    Pausa Activa Recomendada
                </h2>
                <p class="mb-3">Has estado sentado por más de 2 horas. Tu ritmo cardíaco indica sedentarismo.</p>
                <h3 class="h5 mb-3">Ejercicios de Estiramiento - 5 minutos</h3>
                <button class="btn btn-primary px-4" @click="startBreak">
                    <i class="bi bi-play-circle me-2"></i>Iniciar Pausa Activa
                </button>
            </div>
        </div>

        <div class="row g-4">
            <!-- Columna principal de recomendaciones -->
            <div class="col-lg-8">
                <div class="card h-100 shadow-sm">
                    <div class="card-body">
                        <div class="d-flex justify-content-between align-items-center mb-3">
                            <h3 class="card-title h5 mb-0">
                                <i class="bi bi-bullseye text-primary me-2"></i>Recomendaciones Personalizadas
                            </h3>
                            <span class="badge bg-primary">Nuevas: 2</span>
                        </div>

                        <div class="list-group list-group-flush">
                            <div v-for="(recommendation, index) in recommendations" :key="index"
                                class="list-group-item border-light mb-2 rounded-3 hover-effect">
                                <div class="d-flex justify-content-between align-items-center">
                                    <div>
                                        <div class="fw-bold">{{ recommendation.title }}</div>
                                        <div class="small text-muted">{{ recommendation.description }}</div>
                                    </div>
                                    <div class="text-success fw-bold">+{{ recommendation.points }} puntos</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Columna secundaria de estadísticas -->
            <div class="col-lg-4">
                <div class="card h-100 shadow-sm">
                    <div class="card-body">
                        <h3 class="card-title h5 mb-3">
                            <i class="bi bi-graph-up text-primary me-2"></i>Estadísticas del Día
                        </h3>

                        <div class="stats-container">
                            <div class="stat-item text-center p-3 rounded-3">
                                <div class="stat-value text-primary">{{ stats.breaksCompleted }}</div>
                                <div class="stat-label small text-muted">Pausas Realizadas</div>
                            </div>

                            <div class="stat-item text-center p-3 rounded-3">
                                <div class="stat-value text-warning">{{ stats.pointsEarned }}</div>
                                <div class="stat-label small text-muted">Puntos Ganados</div>
                            </div>
                        </div>

                        <div class="progress mt-4" style="height: 8px;">
                            <div class="progress-bar bg-success"
                                :style="{ width: (stats.pointsEarned / stats.dailyGoal * 100) + '%' }"></div>
                        </div>
                        <div class="small text-muted text-center mt-2">
                            {{ Math.round(stats.pointsEarned / stats.dailyGoal * 100) }}% de tu meta diaria
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const recommendations = ref([
    {
        title: "Estiramiento de Cuello",
        description: "Ideal para trabajo de oficina",
        points: 5
    },
    {
        title: "Caminata Corta",
        description: "Reactiva la circulación",
        points: 10
    },
    {
        title: "Ejercicios de respiración",
        description: "Reduce el estrés",
        points: 8
    }
]);

const stats = ref({
    breaksCompleted: 5,
    pointsEarned: 25,
    dailyGoal: 50
});

const startBreak = () => {
    // Lógica para iniciar la pausa activa
    ("");
    Swal.fire({
  title: "Comensando",
  text: "Pausa activa iniciada! Completa los ejercicios para ganar puntos.",
  icon: "success"
});
    // Aquí podrías integrar un contador o redireccionar a otra vista
};
</script>

<style scoped>
.recommendations-container {
    padding: 1rem;
}

.recommendation-card {
    border-left: 4px solid var(--bs-warning);
    border-radius: 0.5rem;
}

.card {
    border: none;
    border-radius: 0.75rem;
}

.hover-effect:hover {
    background-color: rgba(13, 110, 253, 0.05);
    transform: translateY(-2px);
    transition: all 0.2s ease;
    cursor: pointer;
}

.stats-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
}

.stat-item {
    background-color: rgba(248, 249, 250, 0.8);
}

.stat-value {
    font-size: 1.75rem;
    font-weight: 700;
    line-height: 1;
}

.stat-label {
    margin-top: 0.25rem;
}

/* Mejoras para los badges */
.badge {
    font-size: 0.75rem;
    padding: 0.35em 0.65em;
    font-weight: 500;
}
</style>