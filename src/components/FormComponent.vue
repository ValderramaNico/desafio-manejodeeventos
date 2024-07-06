<template>
  <form @submit.prevent>
    <section>
      <div class="inputs">
        <label :class="{ vacio: !paciente }" for="">Paciente</label>
        <input v-model="paciente" type="text" />
      </div>
      <div class="inputs">
        <label :class="{ vacio: !fecha }" for="">Fecha</label>
        <input v-model="fecha" type="date" />
      </div>
      <div class="inputs">
        <label :class="{ vacio: !hora }" for="">Hora</label>
        <input v-model="hora" type="time" />
      </div>
      <div class="inputs">
        <label :class="{ vacio: !gravedad }" for="">Gravedad</label>
        <select v-model="gravedad">
          <option value="baja" class="baja">Baja</option>
          <option value="media" class="media">Media</option>
          <option value="alta" class="alta">Alta</option>
        </select>
      </div>
      <div class="inputs">
        <label :class="{ vacio: !motivo }" for="">Motivo</label>
        <input v-model="motivo" type="text" />
      </div>
    </section>
    <button :disabled="!formularioCompleto()" @click="agregarCita">Agregar</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      paciente: "",
      fecha: "",
      hora: "",
      gravedad: "",
      motivo: "",
    };
  },
  methods: {
    agregarCita() {
      if (this.formularioCompleto()) {
        this.$emit("agregarCita", {
          nombre: this.paciente,
          fecha: this.fecha,
          hora: this.hora,
          gravedad: this.gravedad,
          motivo: this.motivo,
        });
        this.limpiarFormulario();
      } else {
        alert("Todos los campos son obligatorios");
      }
    },
    limpiarFormulario() {
      this.paciente = "";
      this.fecha = "";
      this.hora = "";
      this.gravedad = "";
      this.motivo = "";
    },
    formularioCompleto() {
      return (
        this.paciente && this.fecha && this.hora && this.gravedad && this.motivo
      );
    },
  },
};
</script>

<style scoped>
*body {
  width: auto;
  display: flex;
  flex-direction: column;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1px solid #000;
  border-radius: 15px;
  width: 700px;
}

section {
  display: flex;
  padding: 20px;
  gap: 15px;
}

button {
  width: auto;
  height: auto;
  margin-bottom: 20px;
}

.inputs {
  display: flex;
  flex-direction: column;
}

.vacio {
  font-weight: 700;
  color: red;
}
</style>
