<template>
  <div>
    <div>
      <FormComponent @agregarCita="agregarCita" />
    </div>
    <br>
    <div class="noAppointment" v-if="citas.length === 0">
      <p>No hay consultas registradas.</p>
    </div>
    <div class="appointmentWrapper" v-else>
      <CardComponent
        v-for="(cita, index) in citas"
        :key="index"
        :nombre="cita.nombre"
        :fecha="cita.fecha"
        :hora="cita.hora"
        :motivo="cita.motivo"
        :gravedad="cita.gravedad"
        @eliminarCita="eliminarCita(index)"
      />
    </div>
  </div>
</template>

<script>
import CardComponent from "./components/CardComponent.vue";
import FormComponent from "./components/FormComponent.vue";

export default {
  name: "App",
  components: {
    CardComponent,
    FormComponent,
  },
  data() {
    return {
      citas: [],
    };
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    },
  },
};
</script>

<style>
body {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 3%;
  font-family: sans-serif, Arial, Helvetica;
}

.appointmentWrapper{
display: flex;
flex-wrap: wrap;
gap: 20px;
}

.noAppointment {
  display: flex;
  justify-content: center;
  color: red
}
</style>
