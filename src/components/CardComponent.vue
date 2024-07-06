<template>
  <div>
    <section :class="gravedad">
      <span>
        <h2>Paciente</h2>
        <p>{{ nombre }}</p>
      </span>
      <span>
        <h2>Fecha</h2>
        <p>{{ fecha }}</p>
      </span>
      <span>
        <h2>Hora</h2>
        <p>{{ hora }}</p>
      </span>
      <span>
        <h2>Motivo</h2>
        <p>{{ motivo }}</p>
      </span>
      <button @click="$emit('eliminarCita')">Eliminar</button>
    </section>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: ["nombre", "fecha", "hora", "motivo", "gravedad"],
};
</script>

<style scoped>
section {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  align-items: center;
  width: 250px;
  color: white;
  padding-bottom: 20px;
  border-radius: 15px;
}

button {
  margin-top: 25px;
}

.baja {
  background-color: green;
}

.media {
  background-color: yellow;
  color: black;
}

.alta {
  background-color: red;
}
</style>


