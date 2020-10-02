<template>
  <div class="accounts-app py-lg-5">
    <div
      v-if="isLoading"
      class="loading">
      <div
        class="spinner-border"
        role="status">
        <span class="sr-only">Loading...</span>
      </div>
    </div>
    <div
      v-else
      class="accounts__container container-lg p-0">
      <!-- <indicadores-chile /> -->
      <!-- <div class="d-block d-lg-none p-lg-4 px-4 pt-4 pb-3">
        <multiselect
          v-model="activeAccount"
          :options="accounts"
          :multiple="false"
          :group-select="false"
          track-by="name"
          label="name"
          :searchable="false"
          select-label=""
          deselect-label=""
          selected-label=""
          :allow-empty="false" />
      </div> -->
      <!-- <ul class="accounts__nav nav d-none d-lg-flex">
        <li
          v-for="account in accounts"
          :key="account.id"
          class="nav-item">
          <a
            :class="{active: activeAccount.id == account.id}"
            href="#"
            class="nav-link px-5 py-3"
            @click.prevent="setActiveAccount(account)">{{ account.name }}</a>
        </li>
        <li class="nav-item">
          <a
            href="#"
            class="nav-link px-5 py-3 active">Ahorro</a>
        </li>
        <li class="nav-item">
          <a
            href="#"
            class="nav-link px-5 py-3 disabled">Inversiones</a>
        </li>
        <li class="nav-item">
          <a
            href="#"
            class="nav-link px-5 py-3 disabled">Portafolio</a>
        </li>
      </ul> -->
      <div>
        <div
          v-if="!showPanel"
          class="row no-gutters h-100">
          <div
            class="col-lg-4 d-lg-block"
            :class="!config && !statements ? false : 'd-none'">
            <summary-resume
              :account="activeAccount"
              :indicators="indicators"
              @statements="openStatementsPanel()"
              @config="openConfigPanel()"
              @goto="goToSlide" />
            <!-- <opciones /> -->
            <!-- <test-commons /> -->
          </div>
          <div class="col-lg-8 accounts__investsments-summary">
            <div class="col-lg-12 accounts__investsments-summary">
              <!-- <ul class="accounts__nav nav d-none d-lg-flex">
                <li class="nav-item">
                  <a
                    href="#"
                    class="nav-link px-5 py-3 active">Ahorro</a>
                </li>
                <li class="nav-item">
                  <a
                    href="#"
                    class="nav-link px-5 py-3 disabled">Inversiones</a>
                </li>
                <li class="nav-item">
                  <a
                    href="#"
                    class="nav-link px-5 py-3 disabled">Portafolio</a>
                </li>
              </ul> -->
              <nav>
                <div
                  id="nav-tab"
                  class="nav nav-tabs"
                  role="tablist">
                  <a
                    id="nav-home-tab"
                    class="nav-item nav-link active"
                    data-toggle="tab"
                    href="#nav-home"
                    role="tab"
                    aria-controls="nav-home"
                    aria-selected="true">Comparador</a>
                  <a
                    id="nav-profile-tab"
                    class="nav-item nav-link"
                    data-toggle="tab"
                    href="#nav-profile"
                    role="tab"
                    aria-controls="nav-profile"
                    aria-selected="false">Inversión</a>
                  <a
                    id="nav-contact-tab"
                    class="nav-item nav-link"
                    data-toggle="tab"
                    href="#nav-contact"
                    role="tab"
                    aria-controls="nav-contact"
                    aria-selected="false">Brokers</a>
                  <a
                    id="nav-broker-tab"
                    class="nav-item nav-link"
                    data-toggle="tab"
                    href="#nav-broker"
                    role="tab"
                    aria-controls="nav-broker"
                    aria-selected="false">Brokers</a>
                </div>
              </nav>
              <div
                id="nav-tabContent"
                class="tab-content">
                <div
                  id="nav-home"
                  class="tab-pane fade show active"
                  role="tabpanel"
                  aria-labelledby="nav-home-tab">
                  <formulario />
                </div>
                <div
                  id="nav-profile"
                  class="tab-pane fade"
                  role="tabpanel"
                  aria-labelledby="nav-profile-tab">
                  <listado-gratis />
                </div>
                <div
                  id="nav-contact"
                  class="tab-pane fade"
                  role="tabpanel"
                  aria-labelledby="nav-contact-tab">
                  <listado-pro />
                </div>
                <div
                  id="nav-broker"
                  class="tab-pane fade"
                  role="tabpanel"
                  aria-labelledby="nav-contact-tab">
                  <listado-brokers />
                </div>
              </div>
            </div>
            <!-- <investments-summary
              v-if="!config && !statements"
              class="d-none d-lg-block"
              :account="activeAccount"
              :indicators="indicators"
              @goto="goToSlide" /> -->
            <!-- <formulario /> -->
            <transition name="slide">
              <settings-panel
                v-if="config === true"
                key="config"
                :account="activeAccount"
                @closepanel="closePanel()" />
              <statements-panel
                v-if="statements === true"
                key="statements"
                :account-id="activeAccount.id"
                @closestatementspanel="closeStatementsPanel()" />
            </transition>
          </div>
        </div>
        <div v-if="showPanel">
          <keep-alive>
            <component
              :is="activeSlide"
              :account="activeAccount"
              :investment-type="investmentType"
              @change-investment-type="changeInvestmentType" />
          </keep-alive>
        </div>
      </div>
    </div>
    <investment-modal />
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect';
import { getURLParams } from '@modyo/financial-commons';

import SummaryResume from './components/SummaryResume.vue';
import SettingsPanel from './components/SettingsPanel.vue';
import InvestmentsDetails from './components/InvestmentsDetails.vue';
import InvestmentsSummary from './components/InvestmentsSummary.vue';
import MovementsPanel from './components/MovementsPanel.vue';
import StatementsPanel from './components/StatementsPanel.vue';
import InvestmentModal from './components/InvestmentModal.vue';
import Formulario from './components/Formulario.vue';
import ListadoGratis from './components/ListadoGratis.vue';
import ListadoPro from './components/ListadoPro.vue';
import ListadoBrokers from './components/ListadoBrokers.vue';

export default {
  name: 'Accounts',
  components: {
    'summary-resume': SummaryResume,
    'settings-panel': SettingsPanel,
    'investments-details': InvestmentsDetails,
    'investments-summary': InvestmentsSummary,
    'investment-modal': InvestmentModal,
    'movements-panel': MovementsPanel,
    'statements-panel': StatementsPanel,
    formulario: Formulario,
    'listado-gratis': ListadoGratis,
    'listado-pro': ListadoPro,
    'listado-brokers': ListadoBrokers,
    Multiselect,
  },
  data() {
    return {
      isLoading: true,
      config: false,
      statements: false,
      activeAccount: {},
      activeSlide: 'investments-details',
      investmentType: 'stocks',
      paramAccountId: parseInt(getURLParams('account'), 10),
    };
  },
  computed: {
    localCurrency() {
      return this.$store.state.localCurrency;
    },
    accounts() {
      return this.$store.state.accounts;
    },
    indicators() {
      return this.$store.state.indicators;
    },
    showPanel() {
      return this.$store.state.showPanel;
    },
  },
  watch: {
    accounts() {
      if (this.paramAccountId) {
        this.activeAccount = this.accounts.find((account) => account.id === this.paramAccountId);
      } else {
        [this.activeAccount] = this.accounts;
      }
    },
  },
  created() {
    this.fetchData();
  },
  methods: {
    openConfigPanel() {
      this.config = true;
      this.statements = false;
      this.$store.commit('SET_CURRENT_PAGE', 'settings');
    },
    closePanel() {
      this.config = false;
    },
    openStatementsPanel() {
      this.config = false;
      this.statements = true;
      this.$store.commit('SET_CURRENT_PAGE', 'statements');
    },
    closeStatementsPanel() {
      this.statements = false;
    },
    goToSlide(slide, slug) {
      if (slide === 'investments') {
        this.activeSlide = 'investments-details';
        if (slug) {
          this.investmentType = slug;
        } else {
          this.investmentType = 'stocks';
        }
      } else if (slide === 'movements') {
        this.activeSlide = 'movements-panel';
      }
      this.$store.commit('SET_SHOW_PANEL', true);
      this.$store.commit('SET_CURRENT_PAGE', slug);
    },
    setActiveAccount(account) {
      this.activeAccount = account;
    },
    changeInvestmentType(value) {
      this.investmentType = value;
    },
    fetchData() {
      const vm = this;
      this.isLoading = true;
      this.$store.dispatch('GET_ACCOUNTS')
        .then(() => {
          vm.isLoading = false;
        });
      this.$store.dispatch('GET_INDICATORS');
    },
  },
};
</script>

<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>

<style lang="scss" scoped>
@import "./scss/custom.scss";

.accounts-app {
  min-height: 100%;

  background-color: #fff;
}

@media (min-width: 992px) {
  .accounts-app {
    min-height: auto;

    background-color: transparent;
  }

  .accounts__container {
    background-color: #fff;
  }

  .accounts__nav {
    border-bottom: 1px solid $gray-300;

    .nav-item {
      .nav-link {
        &.active {
          background-color: $primary-10;
          border-bottom: 4px solid $primary;
        }
      }
    }
  }

  .accounts__investsments-summary {
    background-color: $tertiary-20;
  }
}
</style>
