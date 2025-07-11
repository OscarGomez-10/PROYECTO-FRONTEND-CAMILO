<template>
  <div class="container py-4">
    <!-- Métricas -->
    <div class="row g-3 mb-4">
      <div class="col-md-6">
        <div class="card bg-primary text-white">
          <div class="card-body d-flex justify-content-between align-items-center">
            <div>
              <h6>Total Empleados</h6>
              <h3 class="fw-bold">3</h3>
            </div>
            <i class="bi bi-people fs-2"></i>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="card bg-success text-white">
          <div class="card-body d-flex justify-content-between align-items-center">
            <div>
              <h6>Empleados Activos</h6>
              <h3 class="fw-bold">2</h3>
            </div>
            <i class="bi bi-person-check fs-2"></i>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="card bg-purple text-white">
          <div class="card-body d-flex justify-content-between align-items-center">
            <div>
              <h6>Logros Totales</h6>
              <h3 class="fw-bold">3</h3>
            </div>
            <i class="bi bi-award fs-2"></i>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="card bg-warning text-white">
          <div class="card-body d-flex justify-content-between align-items-center">
            <div>
              <h6>Acciones Pendientes</h6>
              <h3 class="fw-bold">3</h3>
            </div>
            <i class="bi bi-bullseye fs-2"></i>
          </div>
        </div>
      </div>
    </div>

    <!-- Top empleados -->
    <div class="card mb-4">
      <div class="card-header fw-bold">Top Empleados</div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item d-flex justify-content-between align-items-center">
          <div class="d-flex align-items-center">
            <div class="rounded-circle bg-primary text-white d-flex justify-content-center align-items-center me-3" style="width: 40px; height: 40px;">
              AG
            </div>
            <div>
              <div class="fw-semibold">Ana García López</div>
              <div class="text-muted small">Desarrolladora Senior</div>
            </div>
          </div>
          <span class="text-warning fw-bold"><i class="bi bi-star-fill me-1"></i>2850</span>
        </li>
        <li class="list-group-item d-flex justify-content-between align-items-center">
          <div class="d-flex align-items-center">
            <div class="rounded-circle bg-primary text-white d-flex justify-content-center align-items-center me-3" style="width: 40px; height: 40px;">
              CR
            </div>
            <div>
              <div class="fw-semibold">Carlos Rodríguez</div>
              <div class="text-muted small">Analista de Datos</div>
            </div>
          </div>
          <span class="text-warning fw-bold"><i class="bi bi-star-fill me-1"></i>2340</span>
        </li>
        <li class="list-group-item d-flex justify-content-between align-items-center">
          <div class="d-flex align-items-center">
            <div class="rounded-circle bg-primary text-white d-flex justify-content-center align-items-center me-3" style="width: 40px; height: 40px;">
              MF
            </div>
            <div>
              <div class="fw-semibold">María Fernández</div>
              <div class="text-muted small">Diseñadora UX</div>
            </div>
          </div>
          <span class="text-warning fw-bold"><i class="bi bi-star-fill me-1"></i>1890</span>
        </li>
      </ul>
    </div>

    <!-- Acciones recientes -->
    <div class="card">
      <div class="card-header fw-bold">Acciones Recientes</div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item d-flex justify-content-between align-items-start">
          <div>
            <div class="fw-semibold">Completar Capacitación</div>
            <div class="text-muted small">Curso de React Avanzado<br>Fecha: 2025-07-08</div>
          </div>
          <span class="badge bg-light text-primary fw-bold">100 pts</span>
        </li>
        <li class="list-group-item d-flex justify-content-between align-items-start">
          <div>
            <div class="fw-semibold">Revisar Código</div>
            <div class="text-muted small">Code Review del proyecto principal<br>Fecha: 2025-07-08</div>
          </div>
          <span class="badge bg-light text-primary fw-bold">50 pts</span>
        </li>
        <li class="list-group-item d-flex justify-content-between align-items-start">
          <div>
            <div class="fw-semibold">Presentación Cliente</div>
            <div class="text-muted small">Demo del nuevo módulo<br>Fecha: 2025-07-10</div>
          </div>
          <span class="badge bg-light text-primary fw-bold">200 pts</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.bg-purple {
  background-color: #9c27b0;
}
</style>
