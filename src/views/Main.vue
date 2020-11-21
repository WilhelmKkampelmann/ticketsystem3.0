<template>
  <section>
    <h1 class="headline">{{ $t('nav.customer-service') }}</h1>
    <form @submit.prevent="clickMe">
    <b-field :label= "$t('main.input1')" label-position="on-border">
      <b-select
      v-model="userInputDatas.selectedKindOfError"
      expanded required>
        <option
        v-for="(option, index) in kindOfError"
        :value="option.value"
        :key="index"
        >
            {{ option.name }}
        </option>
      </b-select>
    </b-field>
    <b-field :label= "$t('main.input2')" label-position="on-border">
      <b-select
      v-model="userInputDatas.selectedUrgency"
      expanded required>
        <option
        :value="option.value"
        v-for="(option, index) in urgency"
        :key="index"
        >
            {{ option.name }}
        </option>
      </b-select>
    </b-field>
    <b-field :label= "$t('main.input3')" label-position="on-border">
            <b-input maxlength="50" type="textarea"
            v-model="userInputDatas.subject" required
            ></b-input>
    </b-field>
    <b-field :label= "$t('main.input4')" label-position="on-border">
            <b-input maxlength="100" type="textarea"
            v-model="userInputDatas.describeError" required
            ></b-input>
    </b-field>
    <b-field :label= "$t('main.input5')" label-position="on-border">
            <b-input v-model="userInputDatas.url" type="text" required
            placeholder="https://...."></b-input>
    </b-field>
    <b-field :label= "$t('main.input6')" grouped label-position="on-border">
            <b-input v-model="userInputDatas.email" required
            type="email"
            placeholder="nobody@nowhere.com"
            expanded>
            </b-input>
            <b-input v-model="userInputDatas.tel"
            placeholder="Telephone number" required
            expanded>
            </b-input>
    </b-field>
    <b-input type="submit" active custom-class="btn">Send</b-input>
    <b-loading :is-full-page="isFullPage"
     v-model="isLoading"
     :can-cancel="true">
     </b-loading>
     <b-notification
      auto-close type="is-success"
      v-model="successIsActive"
      aria-close-label="Close notification">
      Sending was successful
      </b-notification>
      <b-notification
      auto-close type="is-danger"
      v-model="errorIsActive"
      aria-close-label="Close notification">
      There was a Error
      </b-notification>
    </form>
  </section>
</template>

<script>
export default {
  name: 'Main',
  data() {
    return {
      kindOfError: [
        { name: this.$t('main.classic'), value: 'classic' },
        { name: this.$t('main.warning'), value: 'warning' },
        { name: this.$t('main.change'), value: 'changeRequest' },
      ],
      urgency: [
        { name: this.$t('main.red'), value: 'red' },
        { name: this.$t('main.yellow'), value: 'yellow' },
        { name: this.$t('main.green'), value: 'green' },
      ],
      userInputDatas: {
        selectedKindOfError: null,
        selectedUrgency: null,
        subject: '',
        describeError: '',
        url: '',
        email: '',
        tel: '',
      },
      postResponse: [],
      isLoading: false,
      isFullPage: true,
      successIsActive: false,
      errorIsActive: false,
    };
  },
  methods: {
    clickMe() {
      this.isLoading = true;
      this.sendDatas();
      this.clearInputFields();
    },
    async sendDatas() {
      const article = {
        method: 'Post',
        body: JSON.stringify(this.userInputDatas),
      };
      const response = await fetch('https://jsonplaceholder.typicode.com/posts', article);
      const data = await response.json();
      this.postResponse = data;
      if (!response.ok) {
        this.isLoading = false;
        this.errorIsActive = true;
      } else {
        this.isLoading = false;
        this.successIsActive = true;
      }
    },
    clearInputFields() {
      this.userInputDatas.selectedKindOfError = null;
      this.userInputDatas.selectedUrgency = null;
      this.userInputDatas.subject = '';
      this.userInputDatas.describeError = '';
      this.userInputDatas.url = '';
      this.userInputDatas.email = '';
      this.userInputDatas.tel = '';
    },
  },
};
</script>

<style scoped>
section{
    max-width: 90%;
    width: 40%;
    height: 80vh;
    margin: 1.5rem auto;
    text-align: center;
}

.btn{
  border-radius: 10px;
  width: 50%;
  margin: 0 auto;
  text-align: center;
  cursor: pointer;
  color: red;
  background: red;
}

.headline{
  margin: 0 0 1.5rem 0;
  font-weight: bold;
  font-size: 1.2rem;
}

</style>
