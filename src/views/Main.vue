<template>
  <section>
    <b-field label="Select your Error" label-position="on-border" custom-class="b-field">
      <b-select
      v-model="userInputDatas.selectedKindOfError"
      expanded>
        <option
        v-for="(option, index) in kindOfError"
        :value="option.value"
        :key="index"
        >
            {{ option.name }}
        </option>
      </b-select>
    </b-field>
    <b-field label="Select your Urgency" label-position="on-border">
      <b-select
      v-model="userInputDatas.selectedUrgency"
      expanded>
        <option
        :value="option.value"
        v-for="(option, index) in urgency"
        :key="index"
        >
            {{ option.name }}
        </option>
      </b-select>
    </b-field>
    <b-field label="Subject" label-position="on-border">
            <b-input maxlength="50" type="textarea"
            v-model="userInputDatas.subject"
            ></b-input>
    </b-field>
    <b-field label="Describe your Error" label-position="on-border">
            <b-input maxlength="100" type="textarea"
            v-model="userInputDatas.describeError"></b-input>
    </b-field>
    <b-field label="URL" label-position="on-border">
            <b-input v-model="userInputDatas.url"
            placeholder="https://...."></b-input>
    </b-field>
    <b-field label="Contacts" grouped label-position="on-border">
            <b-input v-model="userInputDatas.email"
            type="email"
            placeholder="nobody@nowhere.com"
            expanded>
            </b-input>
            <b-input v-model="userInputDatas.tel"
            placeholder="Telephone numer"
            expanded>
            </b-input>
    </b-field>
    <b-button @click="clickMe" >Send</b-button>
  </section>
</template>

<script>
export default {
  name: 'Main',
  data() {
    return {
      kindOfError: [
        { name: 'Classic', value: 'classic' },
        { name: 'Warning', value: 'warning' },
        { name: 'Change Request', value: 'change' },
      ],
      urgency: [
        { name: 'Red', value: 'red' },
        { name: 'Yellow', value: 'yellow' },
        { name: 'Green', value: 'green' },
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
    };
  },
  methods: {
    clickMe() {
      this.sendDatas();
      this.clearInputFields();
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
    sendDatas() {
      fetch('https://jsonplaceholder.typicode.com/posts', {
        method: 'Post',
        body: JSON.stringify(this.userInputDatas),
      }).then((response) => console.log(response));
    },
  },
};
</script>

<style scoped>
section{
    max-width: 90%;
    width: 45%;
    height: 100vh;
    margin: 1.5rem auto;
}

</style>
