<template>
  <section>
    <b-field label="Select your Error and Urgency" grouped>
      <b-select
      v-model="userInputDatas.kindOfError"
      expanded>
        <option
        v-for="option in kindOfError"
        :value="option.id"
        :key="option.id"
        >
            {{ option.name }}
        </option>
      </b-select>
      <b-select
      v-model="userInputDatas.urgency"
      expanded>
        <option
        v-for="option in urgency"
        :value="option.id"
        :key="option.id"
        >
            {{ option.name }}
        </option>
      </b-select>
    </b-field>
    <b-field label="Subject" >
            <b-input maxlength="50" type="textarea"
            v-model="userInputDatas.subject"></b-input>
    </b-field>
    <b-field label="Describe your Error" >
            <b-input maxlength="100" type="textarea"
            v-model="userInputDatas.describeError"></b-input>
    </b-field>
    <b-field label="URL">
            <b-input v-model="userInputDatas.url"
            placeholder="https://...."></b-input>
    </b-field>
    <b-field label="Contacts" grouped>
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
        kindOfError: '',
        urgency: '',
        subject: '',
        describeError: '',
        url: '',
        email: '',
        tel: '',
      },
    };
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
