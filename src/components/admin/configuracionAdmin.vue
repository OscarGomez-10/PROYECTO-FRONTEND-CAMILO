<template>
    <div class="container py-4">
  <h4 class="mb-4 fw-bold">⚙️ Configuración</h4>

  <div class="row g-4">

    <!-- Configuración de perfil -->
    <div class="col-md-6">
      <div class="card shadow-sm">
        <div class="card-header fw-semibold">Perfil de Usuario</div>
        <div class="card-body">
          <form>
            <div class="mb-3">
              <label class="form-label">Nombre</label>
              <input type="text" class="form-control" value="Oscar Avila" />
            </div>
            <div class="mb-3">
              <label class="form-label">Correo electrónico</label>
              <input type="email" class="form-control" value="oscar@email.com" />
            </div>
            <div class="mb-3">
              <label class="form-label">Nueva contraseña</label>
              <input type="password" class="form-control" />
            </div>
            <button class="btn btn-primary w-100">
              <i class="bi bi-save me-1"></i> Guardar Cambios
            </button>
          </form>
        </div>
      </div>
    </div>

    <!-- Configuraciones generales -->
    <div class="col-md-6">
      <div class="card shadow-sm">
        <div class="card-header fw-semibold">Preferencias Generales</div>
        <div class="card-body">
          <div class="mb-3">
            <label class="form-label">Tema</label>
            <select class="form-select">
              <option selected>Claro</option>
              <option>Oscuro</option>
            </select>
          </div>
          <div class="mb-3">
            <label class="form-label">Idioma</label>
            <select class="form-select">
              <option selected>Español</option>
              <option>Inglés</option>
            </select>
          </div>
          <div class="form-check form-switch mb-3">
            <input class="form-check-input" type="checkbox" id="notificaciones" checked>
            <label class="form-check-label" for="notificaciones">Activar notificaciones</label>
          </div>
          <button class="btn btn-outline-secondary w-100">
            <i class="bi bi-gear me-1"></i> Aplicar Preferencias
          </button>
        </div>
      </div>
    </div>

  </div>
</div>

</template>