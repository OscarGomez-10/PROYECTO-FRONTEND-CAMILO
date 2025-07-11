<template>
    <div class="rewards-tab">
        <!-- Puntos del usuario -->
        <div class="card bg-gradient-primary border-0 mb-4 shadow-sm animate__animated animate__fadeIn">
            <div class="card-body text-center">
                <div class="display-4 fw-bold">{{ userPoints.toLocaleString() }}</div>
                <div class="h5">Puntos Individuales</div>
            </div>
        </div>

        <!-- Progreso del equipo -->
        <div class="card card-custom mb-4 shadow-sm">
            <div class="card-body">
                <h3 class="card-title h5"><i class="bi bi-people-fill me-2"></i>Progreso del Equipo - {{
                    currentTeam.name }}</h3>
                <div class="row text-center mt-3">
                    <div class="col-6">
                        <div class="h3">{{ currentTeam.points.toLocaleString() }}</div>
                        <div class="small opacity-75">Puntos Grupales</div>
                    </div>
                    <div class="col-6">
                        <div class="h3">{{ currentTeam.members }}</div>
                        <div class="small opacity-75">Miembros Activos</div>
                    </div>
                </div>
                <div class="progress mt-3" style="height: 8px;">
                    <div class="progress-bar bg-success" :style="{ width: currentTeam.progress + '%' }"></div>
                </div>
                <p class="small mt-2 mb-0">Progreso hacia {{ currentTeam.nextReward }} ({{
                    currentTeam.goal.toLocaleString() }} puntos)</p>
            </div>
        </div>

        <!-- Pestañas de recompensas -->
        <ul class="nav nav-pills mb-4 justify-content-center">
            <li class="nav-item me-2">
                <button class="nav-link" :class="{ 'active': activeTab === 'individual' }"
                    @click="activeTab = 'individual'">
                    <i class="bi bi-trophy-fill me-1"></i> Individuales
                </button>
            </li>
            <li class="nav-item">
                <button class="nav-link" :class="{ 'active': activeTab === 'group' }" @click="activeTab = 'group'">
                    <i class="bi bi-people-fill me-1"></i> Grupales
                </button>
            </li>
        </ul>

        <!-- Contenido de pestañas -->
        <div class="tab-content">
            <!-- RECOMPENSAS INDIVIDUALES -->
            <div v-if="activeTab === 'individual'" class="animate__animated animate__fadeIn">
                <h3 class="h4 text-center mb-4"><i class="bi bi-trophy-fill me-2"></i>Recompensas Individuales</h3>

                <!-- Por categorías -->
                <div v-for="(category, catIndex) in rewardCategories" :key="'cat-' + catIndex">
                    <h4 class="h5 mb-3" :class="'text-' + category.color">
                        <i :class="'bi bi-' + category.icon + ' me-2'"></i>{{ category.name }}
                    </h4>

                    <div class="row g-4 mb-4">
                        <div class="col-md-4" v-for="(reward, rewardIndex) in filterRewards(category.type)"
                            :key="'reward-' + rewardIndex">
                            <div class="card h-100 shadow-sm reward-card"
                                :class="{ 'locked': userPoints < reward.points }">
                                <div class="card-body text-center">
                                    <div class="display-4 mb-3">{{ reward.emoji }}</div>
                                    <h5 class="card-title">{{ reward.title }}</h5>
                                    <p class="card-text small">{{ reward.description }}</p>
                                    <span class="badge"
                                        :class="userPoints >= reward.points ? 'bg-warning text-dark' : 'bg-secondary'">
                                        {{ reward.points }} puntos
                                    </span>

                                    <button class="btn w-100 mt-3"
                                        :class="userPoints >= reward.points ? 'btn-primary' : 'btn-secondary'"
                                        @click="redeemReward(reward.id)" :disabled="userPoints < reward.points">
                                        {{ getButtonText(reward) }}
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- RECOMPENSAS GRUPALES -->
            <div v-else class="animate__animated animate__fadeIn">
                <h3 class="h4 text-center mb-4"><i class="bi bi-people-fill me-2"></i>Recompensas Grupales</h3>

                <div class="card card-custom mb-4 bg-gradient-info border-0 shadow-sm">
                    <div class="card-body">
                        <h4 class="h5"><i class="bi bi-bullseye me-2"></i>Próxima Meta del Equipo</h4>
                        <div class="row text-center mt-3">
                            <div class="col-6">
                                <div class="h3">{{ currentTeam.progress }}%</div>
                                <div class="small opacity-75">Progreso</div>
                            </div>
                            <div class="col-6">
                                <div class="h3">{{ (currentTeam.goal - currentTeam.points).toLocaleString() }}</div>
                                <div class="small opacity-75">Puntos Restantes</div>
                            </div>
                        </div>
                        <div class="progress mt-3" style="height: 8px;">
                            <div class="progress-bar bg-white" :style="{ width: currentTeam.progress + '%' }"></div>
                        </div>
                        <p class="small mt-2 mb-0">¡Casi llegan al {{ currentTeam.nextReward }}!</p>
                    </div>
                </div>

                <div class="row g-4">
                    <div class="col-md-4" v-for="(reward, index) in groupRewards" :key="'group-reward-' + index">
                        <div class="card h-100 shadow-sm reward-card"
                            :class="{ 'locked': currentTeam.points < reward.points }">
                            <div class="card-body text-center">
                                <div class="display-4 mb-3">{{ reward.emoji }}</div>
                                <h5 class="card-title">{{ reward.title }}</h5>
                                <p class="card-text small">{{ reward.description }}</p>
                                <span class="badge"
                                    :class="currentTeam.points >= reward.points ? 'bg-warning text-dark' : 'bg-secondary'">
                                    {{ reward.points.toLocaleString() }} puntos
                                </span>

                                <div class="progress mt-3" style="height: 6px;"
                                    v-if="currentTeam.points < reward.points">
                                    <div class="progress-bar bg-info"
                                        :style="{ width: Math.min(100, (currentTeam.points / reward.points * 100)) + '%' }">
                                    </div>
                                </div>

                                <button class="btn w-100 mt-3"
                                    :class="currentTeam.points >= reward.points ? 'btn-primary' : 'btn-secondary'"
                                    :disabled="currentTeam.points < reward.points">
                                    {{ currentTeam.points >= reward.points ? 'Canjear' : 'En progreso' }}
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Datos del usuario
const userPoints = ref(1247);
const activeTab = ref('individual');

// Datos del equipo
const currentTeam = ref({
    name: "Desarrollo Frontend",
    points: 3450,
    members: 8,
    goal: 5000,
    progress: 69,
    nextReward: "almuerzo especial"
});

// Categorías de recompensas
const rewardCategories = [
    { name: "Bajo Costo", type: "low", icon: "coin", color: "success" },
    { name: "Costo Medio", type: "medium", icon: "gem", color: "warning" },
    { name: "Alto Costo", type: "high", icon: "fire", color: "danger" }
];

// Todas las recompensas individuales
const individualRewards = ref([
    { id: 1, type: "low", emoji: "☕", title: "Café Gratis", description: "Disfruta de tu bebida favorita", points: 50, status: "available" },
    { id: 2, type: "low", emoji: "🥗", title: "Acceso Prioritario Comedor", description: "Evita las filas en hora pico", points: 100, status: "available" },
    { id: 3, type: "low", emoji: "🌟", title: "Reconocimiento Digital", description: "Aparece en el muro interno", points: 75, status: "available" },
    { id: 4, type: "medium", emoji: "🌴", title: "Medio Día Libre", description: "Descansa y disfruta tu tiempo", points: 500, status: "available" },
    { id: 5, type: "medium", emoji: "🍔", title: "Bono Apps Comida", description: "$20 USD para delivery", points: 400, status: "available" },
    { id: 6, type: "medium", emoji: "🎁", title: "Entrada a Rifa Mensual", description: "Participa por premios increíbles", points: 300, status: "available" },
    { id: 7, type: "high", emoji: "🏖️", title: "Día Libre Completo", description: "Día libre adicional", points: 1000, status: "coming" },
    { id: 8, type: "high", emoji: "🎧", title: "Audífonos Ergonómicos", description: "Mejora tu experiencia de trabajo", points: 1500, status: "coming" },
    { id: 9, type: "high", emoji: "🏋️", title: "Membresía Gimnasio", description: "3 meses de acceso completo", points: 2000, status: "coming" }
]);

// Recompensas grupales
const groupRewards = ref([
    { id: 101, emoji: "🍽️", title: "Almuerzo Especial", description: "Comida patrocinada por la empresa", points: 5000, progress: 69 },
    { id: 102, emoji: "🏠", title: "Día Remoto Adicional", description: "Trabajo desde casa para todo el equipo", points: 8000, progress: 43 },
    { id: 103, emoji: "🎮", title: "Escape Room", description: "Actividad recreativa grupal", points: 12000, progress: 29 },
    { id: 104, emoji: "🎨", title: "Decoración de Oficina", description: "Presupuesto para personalizar espacio", points: 15000, progress: 23 },
    { id: 105, emoji: "🧘", title: "Día de Bienestar", description: "Masajes, yoga y meditación grupal", points: 20000, progress: 17 },
    { id: 106, emoji: "🏞️", title: "Excursión Corporativa", description: "Paseo con todo incluido", points: 35000, progress: 10 }
]);

// Filtrar recompensas por categoría
const filterRewards = (type) => {
    return individualRewards.value.filter(reward => reward.type === type);
};

// Texto del botón según estado
const getButtonText = (reward) => {
    if (userPoints.value < reward.points) return 'Faltan puntos';
    if (reward.status === 'coming') return 'Próximamente';
    return 'Canjear';
};

// Canjear recompensa
const redeemReward = (rewardId) => {
    const reward = individualRewards.value.find(r => r.id === rewardId);
    if (reward && userPoints.value >= reward.points) {
        alert(`¡Recompensa canjeada: ${reward.title}!`);
        userPoints.value -= reward.points;
    }
};
</script>

<style scoped>
.rewards-tab {
    padding: 1rem;
}

.card {
    border-radius: 0.75rem;
    transition: all 0.3s ease;
}

.reward-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
}

.reward-card.locked {
    opacity: 0.8;
}

.nav-pills .nav-link {
    transition: all 0.3s ease;
    border-radius: 50px;
    padding: 8px 20px;
}

.nav-pills .nav-link.active {
    background-color: var(--bs-primary);
    color: white !important;
    font-weight: 500;
}

.bg-gradient-primary {
    background: linear-gradient(135deg, #0d6efd, #0b5ed7);
}

.bg-gradient-info {
    background: linear-gradient(135deg, #0dcaf0, #0ba8d7);
    color: white;
}

.badge {
    font-weight: 500;
    padding: 5px 10px;
    border-radius: 50px;
}

.progress {
    border-radius: 50px;
    background-color: #e9ecef;
}

.btn {
    border-radius: 50px;
    font-weight: 500;
    transition: all 0.3s ease;
}

.btn:disabled {
    opacity: 0.7;
}
</style>