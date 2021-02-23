<template>
  <validation-provider
    :name="fieldObj.placeholder"
    :mode="validationMode"
    :rules="fieldObj.validationRules"
    v-slot="{classes, errors}"
    tag="div"
  >
    <label class="validated-form__field"
      :class="classes"
    >
      <div class="validated-form__screed"
        :class="'validated-form__screed--' + fieldObj.type"
      >
        <input class="validated-form__input"
          v-model="value"
          :id="fieldObj.name"
          :name="fieldObj.name"
          :type="fieldObj.type"
          :placeholder="fieldObj.placeholder"
        >
      </div>
      <span class="validated-form__hint">{{errors[0]}}</span>
    </label>
  </validation-provider>
</template>

<script>
  import {ValidationProvider} from "vee-validate";

  export default {
    data() {
      return {
        validationMode: 'lazy',
        value: '',
      }
    },
    props: {
      'field-obj': Object,
      'index': Number,
    },
    components: {
      ValidationProvider,
    }
  }
</script>