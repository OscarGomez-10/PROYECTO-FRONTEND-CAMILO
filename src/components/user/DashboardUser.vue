<template>
  <!-- Dashboard Tab -->
  <div class="tab-pane fade show active" id="dashboard">
    <div class="row g-4 mb-4">
      <!-- Primera fila de 2 columnas -->
      <div class="col-md-6">
        <div class="card card-large h-100">
          <div class="card-body">
            <h3 class="card-title h4"><i class="bi bi-person-running me-2"></i>Pausas Hoy</h3>
            <div class="row text-center mt-4">
              <div class="col-6">
                <div class="h2 text-primary">5</div>
                <div class="small opacity-75">Completadas</div>
              </div>
              <div class="col-6">
                <div class="h2">2</div>
                <div class="small opacity-75">Pendientes</div>
              </div>
            </div>
            <div class="progress progress-custom mt-4">
              <div class="progress-bar progress-fill-custom" style="width: 70%"></div>
            </div>
            <p class="small mt-3 mb-0">70% del objetivo diario</p>
          </div>
        </div>
      </div>

      <div class="col-md-6">
        <div class="card card-large h-100">
          <div class="card-body text-center">
            <h3 class="card-title h4"><i class="bi bi-star-fill me-2"></i>Puntos Totales</h3>
            <div class="display-4 text-warning my-4">1,247</div>
            <p class="h5 mb-4">+25 puntos hoy</p>
            <button class="btn btn-secondary btn-lg w-100">Ver Recompensas</button>
          </div>
        </div>
      </div>

      <!-- Segunda fila de 2 columnas -->
      <div class="col-md-6">
        <div class="card card-large h-100">
          <div class="card-body">
            <h3 class="card-title h4"><i class="bi bi-graph-up-arrow me-2"></i>Productividad</h3>
            <div class="row text-center mt-4">
              <div class="col-6">
                <div class="h2 text-success">92%</div>
                <div class="small opacity-75">Eficiencia</div>
              </div>
              <div class="col-6">
                <div class="h2">4.2</div>
                <div class="small opacity-75">Horas Focus</div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="col-md-6">
        <div class="card card-large h-100">
          <div class="card-body">
            <h3 class="card-title h4"><i class="bi bi-heart-pulse-fill me-2"></i>Estado de Salud</h3>
            <div class="row mt-4">
              <div class="col-6 mb-4">
                <div class="metric-value">72</div>
                <div class="small opacity-75">BPM</div>
                <span class="badge status-good mt-2">Normal</span>
              </div>
              <div class="col-6 mb-4">
                <div class="metric-value">6,847</div>
                <div class="small opacity-75">Pasos</div>
                <span class="badge status-warning mt-2">Bajo</span>
              </div>
            </div>
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
.card-large {
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  min-height: 280px;
}

.card-large:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.card-title {
  font-size: 1.35rem;
  margin-bottom: 1.5rem;
}

.metric-value {
  font-size: 2.5rem;
  font-weight: bold;
  margin: 10px 0;
}

.status-good {
  background-color: #28a745;
  color: white;
  font-size: 0.9rem;
  padding: 5px 12px;
  border-radius: 50px;
}

.status-warning {
  background-color: #ffc107;
  color: black;
  font-size: 0.9rem;
  padding: 5px 12px;
  border-radius: 50px;
}

.progress-custom {
  height: 10px;
  border-radius: 5px;
  margin: 20px 0;
}

.progress-fill-custom {
  background-color: #0d6efd;
  border-radius: 5px;
}

.display-4 {
  font-size: 3rem;
  font-weight: bold;
}

.btn-lg {
  padding: 10px 20px;
  font-size: 1.1rem;
}

/* Ajustes responsivos */
@media (max-width: 768px) {
  .card-large {
    min-height: auto;
  }
  
  .display-4 {
    font-size: 2.5rem;
  }
  
  .metric-value {
    font-size: 2rem;
  }
}
</style>