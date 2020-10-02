<template>
  <div class="container mt-2">
    <h1 class="principal-title">
      ¿Dónde invertir?
    </h1>
    <p class="principal-subtitle">
      Éstas son nuestras recomendaciones para ti
    </p>
    <div class="row">
      <div
        class="col-12 col-sm-6 col-md-6 col-lg-3 item pro"
        data-producttype="ahorro">
        <div class="card item-card card-block">
          <img
            class="bank-image"
            src="https://d7nxjt1whovz0.cloudfront.net/marketplace/logos/divisions/banco-de-chile.png"
            alt="Photo of sunset">
          <h5 class="item-card-title mt-3 mb-3">
            Ahorro Reajustable Giro Diferido
          </h5>
          <ul class="card-text">
            <li>Modo de cuenta: Electrónica</li>
            <li>Giros máximos: 6</li>
            <li>Tipo de cuenta: Giro Diferido</li>
          </ul>
          <p class="card-tasa">
            UF + 0,5%
          </p>
          <button
            type="button"
            class="btn btn-primary rounded bg-green">
            Solicitar
          </button>
        </div>
      </div>
    </div><div class="row">
      <div
        data-producttype="ahorro"
        class="col-12 col-sm-6 col-md-6 col-lg-3 item">
        <div class="card item-card card-block">
          <img
            class="bank-image"
            src="https://d7nxjt1whovz0.cloudfront.net/marketplace/logos/divisions/banco-estado.png"
            alt="Photo of sunset">
          <h5 class="item-card-title mt-3 mb-3">
            Cuenta de Ahorro Vivienda Electrónica
          </h5>
          <ul class="card-text">
            <li>Modo de cuenta: Electrónica</li>
            <li>Giros máximos: 6</li>
            <li>Tipo de cuenta: Giro Diferido</li>
          </ul>
          <button
            type="button"
            class="btn btn-primary rounded bg-green">
            Solicitar
          </button>
        </div>
      </div>
      <div
        class="col-12 col-sm-6 col-md-6 col-lg-3 item"
        data-producttype="fondo">
        <div class="card item-card card-block">
          <img
            class="bank-image"
            src="https://s3.amazonaws.com/marketplace.comparaonline.com/marketplace/logos/divisions/coopeuch.png"
            alt="Photo of sunset">
          <h5 class="item-card-title mt-3 mb-3">
            Cuenta de Ahorro para la Vivienda
          </h5>
          <ul class="card-text">
            <li>Modo de cuenta: Electrónica</li>
            <li>Giros máximos: 6</li>
            <li>Tipo de cuenta: Giro Diferido</li>
          </ul>
          <button
            type="button"
            class="btn btn-primary rounded bg-green">
            Solicitar
          </button>
        </div>
      </div>
      <div
        class="col-12 col-sm-6 col-md-6 col-lg-3 item"
        data-producttype="ahorro">
        <div class="card item-card card-block">
          <img
            class="bank-image"
            src="https://d7nxjt1whovz0.cloudfront.net/marketplace/logos/divisions/banco-falabella.png"
            alt="Photo of sunset">
          <h5 class="item-card-title  mt-3 mb-3">
            Cuenta de Ahorro
          </h5>
          <ul class="card-text">
            <li>Modo de cuenta: Electrónica</li>
            <li>Giros máximos: 6</li>
            <li>Tipo de cuenta: Giro Diferido</li>
          </ul>
          <button
            type="button"
            class="btn btn-primary rounded bg-green">
            Solicitar
          </button>
        </div>
      </div>
      <div
        class="col-12 col-sm-6 col-md-6 col-lg-3 item"
        data-producttype="ahorro">
        <div class="card item-card card-block">
          <img
            class="bank-image"
            src="https://d7nxjt1whovz0.cloudfront.net/marketplace/logos/divisions/banco-de-chile.png"
            alt="Photo of sunset">
          <h5 class="item-card-title mt-3 mb-3">
            Ahorro Reajustable Giro Diferido
          </h5>
          <ul class="card-text">
            <li>Modo de cuenta: Electrónica</li>
            <li>Giros máximos: 6</li>
            <li>Tipo de cuenta: Giro Diferido</li>
          </ul>
          <button
            type="button"
            class="btn btn-primary rounded bg-green">
            Solicitar
          </button>
        </div>
      </div>
      <button
        id="more"
        onclick="seeMore()"
        class="buton-see-more">
        Ver más
      </button>
      <!--More options -->
      <div
        id="hiddenCards"
        class="d-none row w-100">
        <div
          class="col-12 col-sm-6 col-md-6 col-lg-3 item"
          data-producttype="deposito">
          <div class="card item-card card-block">
            <img
              class="bank-image"
              src="https://d7nxjt1whovz0.cloudfront.net/marketplace/logos/divisions/banco-de-chile.png"
              alt="Photo of sunset">
            <h5 class="item-card-title mt-3 mb-3">
              Ahorro Reajustable Giro Diferido
            </h5>
            <ul class="card-text">
              <li>Modo de cuenta: Electrónica</li>
              <li>Giros máximos: 6</li>
              <li>Tipo de cuenta: Giro Diferido</li>
            </ul>
            <button
              type="button"
              class="btn btn-primary rounded bg-green">
              Solicitar
            </button>
          </div>
        </div>
        <div
          class="col-12 col-sm-6 col-md-6 col-lg-3 item"
          data-producttype="fondo">
          <div class="card item-card card-block">
            <img
              class="bank-image"
              src="https://d7nxjt1whovz0.cloudfront.net/marketplace/logos/divisions/banco-de-chile.png"
              alt="Photo of sunset">
            <h5 class="item-card-title mt-3 mb-3">
              Ahorro Reajustable Giro Diferido
            </h5>
            <ul class="card-text">
              <li>Modo de cuenta: Electrónica</li>
              <li>Giros máximos: 6</li>
              <li>Tipo de cuenta: Giro Diferido</li>
            </ul>
            <button
              type="button"
              class="btn btn-primary rounded bg-green">
              Solicitar
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import $ from 'jquery';

export default {
  name: 'ListadoPro',
};

</script>

<style lang="scss" scoped>
@import "../scss/variables.scss";
@import "../scss/custom_vass.scss";

</style>
