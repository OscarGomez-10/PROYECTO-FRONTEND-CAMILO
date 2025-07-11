<template>
    <div class="health-container">
        <div class="row g-4">
            <!-- Primera fila de 2 columnas -->
            <div class="col-md-6">
                <div class="card card-large h-100">
                    <div class="card-body">
                        <h3 class="card-title h4"><i class="bi bi-heart-pulse-fill me-2"></i>Ritmo Cardíaco</h3>
                        <div class="metric-value">72 BPM</div>
                        <span class="badge status-good mb-3">Estado Normal</span>
                        <div class="progress progress-custom">
                            <div class="progress-bar progress-fill-custom" style="width: 60%"></div>
                        </div>
                        <p class="small mt-2 mb-0">Promedio últimas 8 horas</p>
                    </div>
                </div>
            </div>

            <div class="col-md-6">
                <div class="card card-large h-100">
                    <div class="card-body">
                        <h3 class="card-title h4"><i class="bi bi-person-walking me-2"></i>Actividad Física</h3>
                        <div class="metric-value">6,847</div>
                        <div class="small opacity-75 mb-2">Pasos hoy</div>
                        <span class="badge status-warning mb-3">Necesita movimiento</span>
                        <div class="progress progress-custom">
                            <div class="progress-bar progress-fill-custom" style="width: 40%"></div>
                        </div>
                        <p class="small mt-2 mb-0">Meta: 10,000 pasos</p>
                    </div>
                </div>
            </div>

            <!-- Segunda fila de 2 columnas -->
            <div class="col-md-6">
                <div class="card card-large h-100">
                    <div class="card-body">
                        <h3 class="card-title h4"><i class="bi bi-stopwatch-fill me-2"></i>Tiempo Sedentario</h3>
                        <div class="metric-value">2.5h</div>
                        <div class="small opacity-75 mb-2">Sin movimiento</div>
                        <span class="badge status-alert mb-3">Crítico</span>
                        <p class="small mt-2 mb-0">Recomendado: máximo 2 horas</p>
                    </div>
                </div>
            </div>

            <div class="col-md-6">
                <div class="card card-large h-100">
                    <div class="card-body">
                        <h3 class="card-title h4"><i class="bi bi-emoji-frown-fill me-2"></i>Nivel de Estrés</h3>
                        <div class="metric-value">Medio</div>
                        <span class="badge status-warning mb-3">Monitoreando</span>
                        <div class="progress progress-custom">
                            <div class="progress-bar progress-fill-custom" style="width: 55%"></div>
                        </div>
                        <p class="small mt-2 mb-0">Basado en variabilidad cardíaca</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
// Lógica del componente (si es necesaria)
</script>

<style scoped>
.health-container {
    padding: 20px;
}

.card-large {
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    min-height: 250px;
    /* Altura mínima aumentada */
}

.card-large:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.card-title {
    font-size: 1.25rem;
    margin-bottom: 1rem;
}

.metric-value {
    font-size: 2.5rem;
    /* Tamaño aumentado */
    font-weight: bold;
    margin: 15px 0;
    /* Espaciado aumentado */
}

.status-good {
    background-color: #28a745;
    color: white;
    font-size: 0.9rem;
    padding: 5px 10px;
}

.status-warning {
    background-color: #ffc107;
    color: black;
    font-size: 0.9rem;
    padding: 5px 10px;
}

.status-alert {
    background-color: #dc3545;
    color: white;
    font-size: 0.9rem;
    padding: 5px 10px;
}

.progress-custom {
    height: 10px;
    /* Altura aumentada */
    border-radius: 5px;
    margin: 20px 0;
    /* Espaciado aumentado */
}

.progress-fill-custom {
    background-color: #0d6efd;
    border-radius: 5px;
}

.small {
    font-size: 0.85rem;
}

/* Ajustes responsivos */
@media (max-width: 768px) {
    .card-large {
        min-height: auto;
    }

    .metric-value {
        font-size: 2rem;
    }
}
</style>