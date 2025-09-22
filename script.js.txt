// Funções de Modal
function openModal(modalId) {
    const modal = document.getElementById(`${modalId}-modal`);
    if (modal) {
        modal.style.display = 'flex';
    }
}

function closeModal(modalId) {
    const modal = document.getElementById(modalId);
    if (modal) {
        modal.style.display = 'none';
    }
}

// Função para alternar abas
function initializeTabs() {
    const tabTriggers = document.querySelectorAll('.tab-trigger');
    const tabContents = document.querySelectorAll('.tab-content');

    tabTriggers.forEach(trigger => {
        trigger.addEventListener('click', () => {
            const target = trigger.getAttribute('data-tab');

            tabTriggers.forEach(t => t.classList.remove('active'));
            tabContents.forEach(c => c.classList.remove('active'));

            trigger.classList.add('active');
            document.getElementById(`tab-${target}`).classList.add('active');
        });
    });
}

// Função para carregar dados iniciais do dashboard
function loadDashboardData() {
    // Aqui você pode adicionar dados reais se quiser
    const recentReservations = document.getElementById('recent-reservations');
    recentReservations.innerHTML = `
        <div>Reserva: João - 15/09 19:00 - 2 pessoas</div>
        <div>Reserva: Maria - 16/09 20:00 - 4 pessoas</div>
        <div>Reserva: Carlos - 17/09 18:30 - 3 pessoas</div>
    `;

    const confirmedReservations = document.getElementById('confirmed-reservations');
    confirmedReservations.innerHTML = `
        <div>Reserva: Ana - 12/09 19:00 - 2 pessoas</div>
        <div>Reserva: Bruno - 13/09 20:30 - 1 pessoa</div>
    `;

    const pendingReservations = document.getElementById('pending-reservations');
    pendingReservations.innerHTML = `
        <div>Reserva: Felipe - 18/09 21:00 - 5 pessoas</div>
        <div>Reserva: Larissa - 19/09 19:30 - 2 pessoas</div>
    `;
}

// Função para inicializar o calendário (placeholder)
function initializeDashboardCalendar() {
    const calendar = document.getElementById('dashboard-calendar');
    if (calendar) {
        calendar.innerHTML = `<p>Calendário de reservas será exibido aqui.</p>`;
    }
}

// Inicialização quando a página carregar
document.addEventListener('DOMContentLoaded', function() {
    loadDashboardData();
    initializeDashboardCalendar();
    initializeTabs();
});

// Envio do formulário de nova reserva
const newReservationForm = document.getElementById('new-reservation-form');
if (newReservationForm) {
    newReservationForm.addEventListener('submit', function(e) {
        e.preventDefault();
        alert('Reserva criada com sucesso!');
        closeModal('new-reservation-modal');
        newReservationForm.reset();
    });
}
