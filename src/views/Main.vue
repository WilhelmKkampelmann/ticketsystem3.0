<template>
  <section>
    <h3>Customer Service</h3>
    <b-field label="Simple">
      <b-select placeholder="Select an Error">
        <option
        v-for="option in kindOfError"
        :value="option.id"
        :key="option.id"
        >
            {{ option.name }}
        </option>
      </b-select>
    </b-field>
    <b-field label="Simple">
      <b-select placeholder="Select an Urgency">
        <option
        v-for="option in urgency"
        :value="option.id"
        :key="option.id"
        >
            {{ option.name }}
        </option>
      </b-select>
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

    };
  },
};
</script>

<style scoped>
</style>
