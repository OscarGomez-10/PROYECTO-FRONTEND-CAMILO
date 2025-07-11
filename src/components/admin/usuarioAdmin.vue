<template>
  <div class="container mt-4">
    <div class="d-flex justify-content-between align-items-center mb-4">
      <h4 class="fw-bold m-0">Gestión de Empleados</h4>
      <div class="d-flex gap-2">
        <button class="btn btn-outline-secondary d-flex align-items-center">
          <i class="bi bi-funnel me-2"></i>
          Filtrar
        </button>
        <button type="button" class="btn btn-primary d-flex align-items-center" data-bs-toggle="modal"
          data-bs-target="#exampleModal">
          <i class="bi bi-plus-lg me-1"></i>
          Agregar empleado
        </button>
      </div>
    </div>
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header bg-primary text-white">
            <h1 class="modal-title fs-5" id="exampleModalLabel">Agregar Empleado</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">

            <div class="row">
              <div class="col-md-12">
                <label for="nombre"> Nombre del usuario:</label>
                <input type="text" name="" class="form-control" />
              </div>
            </div>

            <div class="col-md-12">
              <label for="nombre"> Cargo del usuario:</label>
              <input type="text" name="" class="form-control" />
            </div>
            <div class="col-md-12">
              <label for="nombre"> Departamento del usuario:</label>
              <input type="text" name="" class="form-control" />
            </div>
            <div class="col-md-12">
              <label for="nombre"> Puntos del usuario:</label>
              <input type="number" name="" class="form-control" />
            </div>
            <div class="col-md-12">
              <label for="nombre">Nivel del usuario:</label>
              <select id="tipo_mascota" class="form-select" aria-label="Default select example">
                <option selected value="">Selecciona por defecto</option>
                <option value="Experto">Experto</option>
                <option value="Avanzado">Avanzado</option>
                <option value="Intermedio">Intermedio</option>

              </select>
            </div>
            <div class="col-md-12">
              <label for="nombre">Estado del usuario:</label>
              <select id="tipo_mascota" class="form-select" aria-label="Default select example">
                <option selected value="">Selecciona por defecto</option>
                <option value="Activo">Activo</option>
                <option value="Pausa">Pausa</option>
              </select>
            </div>

          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
            <button id="save" onclick="guardar()" class="btn btn-primary">Guardar </button>
          </div>
        </div>
      </div>
    </div>
    <div class="table-responsive">
      <table class="table table-hover border  align-middle ">
        <thead class="table-light">
          <tr>
            <th>Empleado</th>
            <th>Cargo</th>
            <th>Departamento</th>
            <th>Puntos</th>
            <th>Nivel</th>
            <th>Estado</th>
            <th>Acciones</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Ana García López</td>
            <td>Desarrolladora Senior</td>
            <td>IT</td>
            <td><i class="bi bi-star text-warning"></i> 2850</td>
            <td><span class="badge bg-secondary">Experto</span></td>
            <td><span class="badge bg-success">Activo</span></td>
            <td><a href="#"><i class="bi bi-chevron-right text-primary text-dark"></i></a></td>
          </tr>
          <tr>
            <td>Carlos Rodríguez</td>
            <td>Analista de Datos</td>
            <td>Analytics</td>
            <td><i class="bi bi-star text-warning"></i> 2340</td>
            <td><span class="badge bg-primary">Avanzado</span></td>
            <td><span class="badge bg-success">Activo</span></td>
            <td><a href="#"><i class="bi bi-chevron-right text-primary text-dark"></i></a></td>
          </tr>
          <tr>
            <td>María Fernández</td>
            <td>Diseñadora UX</td>
            <td>Diseño</td>
            <td><i class="bi bi-star text-warning"></i> 1890</td>
            <td><span class="badge bg-info">Intermedio</span></td>
            <td><span class="badge bg-warning text-dark">Pausa</span></td>
            <td><a href="#"><i class="bi bi-chevron-right text-primary text-dark"></i></a></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
