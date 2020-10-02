<template>
  <form
    id="initialData"
    class="form-data">
    <div class="group">
      <input
        type="text"
        required>
      <span class="highlight" />
      <span class="bar" />
      <label>¿Cómo te llamas?</label>
    </div>

    <div class="group">
      <input
        type="text"
        required>
      <span class="highlight" />
      <span class="bar" />
      <label>¿Cuál es tu RUT?</label>
    </div>

    <div class="group">
      <input
        type="number"
        required>
      <span class="highlight" />
      <span class="bar" />
      <label>¿Cuántos años tienes?</label>
    </div>

    <div class="group">
      <input
        type="number"
        required>
      <span class="highlight" />
      <span class="bar" />
      <label>¿Cuál es tu email?</label>
    </div>

    <div class="group">
      <input
        type="text"
        required>
      <span class="highlight" />
      <span class="bar" />
      <label>Escribe tu contraseña</label>
    </div>

    <div class="group">
      <input
        type="text"
        required>
      <span class="highlight" />
      <span class="bar" />
      <label>Confirma tu contraseña</label>
    </div>
    <div class="buttons">
      <button
        id="´rev"
        type="button"
        class="btn btn-primary rounded bg-green">
        Anterior
      </button>
      <button
        id="next"
        type="button"
        class="btn btn-primary rounded bg-green">
        siguiente
      </button>
    </div>
  </form>
</template>
<script>
// import $ from 'jquery';

export default {
  name: 'Formulario',
};

</script>

<style lang="scss" scoped>
@import "../scss/variables.scss";
@import "../scss/custom_vass.scss";

</style>
