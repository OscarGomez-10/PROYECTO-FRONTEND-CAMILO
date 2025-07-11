<template>
    <div class="container py-4">
  <h4 class="mb-4 fw-bold">📊 Reportes de Actividad</h4>

  <!-- Filtro de fecha -->
  <div class="d-flex flex-wrap gap-3 mb-4">
    <div>
      <label class="form-label mb-0">Desde</label>
      <input type="date" class="form-control" />
    </div>
    <div>
      <label class="form-label mb-0">Hasta</label>
      <input type="date" class="form-control" />
    </div>
    <div class="align-self-end">
      <button class="btn btn-outline-primary">
        <i class="bi bi-funnel me-1"></i> Filtrar
      </button>
    </div>
  </div>

  <!-- Tabla resumen -->
  <div class="table-responsive mb-4">
    <table class="table table-striped table-hover">
      <thead class="table-primary">
        <tr>
          <th>Empleado</th>
          <th>Acciones Completadas</th>
          <th>Puntos Ganados</th>
          <th>Última Actividad</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Ana García</td>
          <td>12</td>
          <td>1150</td>
          <td>2025-07-09</td>
        </tr>
        <tr>
          <td>Carlos Rodríguez</td>
          <td>8</td>
          <td>890</td>
          <td>2025-07-08</td>
        </tr>
        <tr>
          <td>María Fernández</td>
          <td>15</td>
          <td>1420</td>
          <td>2025-07-09</td>
        </tr>
      </tbody>
    </table>
  </div>

  
</div>

</template>