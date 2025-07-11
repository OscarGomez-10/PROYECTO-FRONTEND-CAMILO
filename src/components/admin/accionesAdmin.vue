<template>
  <div class="container py-4">

 
    <div class="d-flex justify-content-between align-items-center mb-4">
      <h4 class="fw-bold">Pausas Activas</h4>
      <button class="btn bg-primary text-white" data-bs-toggle="modal" data-bs-target="#modalAgregar">
        <i class="bi bi-plus-circle me-1"></i> Nueva Pausa
      </button>
    </div>


    <div class="row g-4">
      <div class="col-md-4" v-for="pausa in pausas" :key="pausa.titulo">
        <div class="card h-100 shadow-sm">
          <div class="card-body d-flex flex-column">
            <div class="d-flex align-items-center mb-3">
              <i :class="`bi ${pausa.icono} fs-1 ${pausa.color} me-3`"></i>
              <div>
                <h5 class="card-title mb-0">{{ pausa.titulo }}</h5>
                <small class="text-muted">Duración: {{ pausa.duracion }}</small>
              </div>
            </div>
            <p class="card-text">{{ pausa.descripcion }}</p>
            <div class="mt-auto">
              <button :class="`btn ${pausa.boton} w-100`" @click="abrirModal(pausa)">
                <i class="bi bi-play-circle me-1"></i> Iniciar
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>


    <div class="modal fade" id="modalPausa" tabindex="-1" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header bg-primary text-white ">
            <h5 class="modal-title">{{ titulo }}</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
          </div>
          <div class="modal-body text-center">
            <h5 class="mb-3">¿Listo para comenzar esta pausa?</h5>
            <p class="text-muted">{{ descripcion }}</p>
            <p><strong>Duración:</strong> {{ duracion }}</p>
          </div>
          <div class="modal-footer">
            <button class="btn bg-primary text-white" data-bs-dismiss="modal">Comenzar</button>
            <button class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          </div>
        </div>
      </div>
    </div>

  
    <div class="modal fade" id="modalAgregar" tabindex="-1" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header bg-primary text-white">
            <h5 class="modal-title">Agregar Nueva Pausa</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
          </div>
          <div class="modal-body">
            <div class="mb-3">
              <label class="form-label">Título</label>
              <input type="text" class="form-control" placeholder="Ej: Respiración Profunda" />
            </div>
            <div class="mb-3">
              <label class="form-label">Descripción</label>
              <textarea class="form-control" rows="3" placeholder="Describe la pausa..."></textarea>
            </div>
            <div class="mb-3">
              <label class="form-label">Duración</label>
              <input type="text" class="form-control" placeholder="Ej: 5 min" />
            </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-primary ">Guardar</button>
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const titulo = ref('')
const descripcion = ref('')
const duracion = ref('')
let modalInstance = null

function abrirModal(info) {
  titulo.value = info.titulo
  descripcion.value = info.descripcion
  duracion.value = info.duracion

  modalInstance = new bootstrap.Modal(document.getElementById('modalPausa'))
  modalInstance.show()
}

const pausas = [
  {
    titulo: 'Estiramiento Básico',
    descripcion: 'Activa tu cuerpo con una rutina rápida de estiramientos para cuello, brazos y espalda.',
    duracion: '5 min',
    icono: 'bi-person-fill-up',
    color: 'text-primary',
    boton: 'btn-outline-primary'
  },
  {
    titulo: 'Baile Libre',
    descripcion: 'Suelta el estrés bailando con música energética. ¡Muévete como quieras!',
    duracion: '7 min',
    icono: 'bi-music-note-beamed',
    color: 'text-success',
    boton: 'btn-outline-success'
  },
  {
    titulo: 'Respiración Guiada',
    descripcion: 'Respira profundo y reduce la ansiedad con una pausa de respiración consciente.',
    duracion: '3 min',
    icono: 'bi-bullseye',
    color: 'text-danger',
    boton: 'btn-outline-danger'
  },
  {
    titulo: 'Descanso Visual',
    descripcion: 'Relaja tus ojos alejando la vista de la pantalla y enfocando objetos distantes.',
    duracion: '2 min',
    icono: 'bi-eye',
    color: 'text-info',
    boton: 'btn-outline-info'
  },
  {
    titulo: 'Toma de Agua',
    descripcion: 'Toma un vaso de agua para mantenerte hidratado y mejorar tu concentración.',
    duracion: '1 min',
    icono: 'bi-cup-hot',
    color: 'text-warning',
    boton: 'btn-outline-warning text-dark'
  },
  {
    titulo: 'Ejercicio Facial',
    descripcion: 'Relaja el rostro con movimientos suaves que alivian la tensión de mandíbula y frente.',
    duracion: '4 min',
    icono: 'bi-emoji-smile',
    color: 'text-secondary',
    boton: 'btn-outline-secondary'
  }
]
</script>
