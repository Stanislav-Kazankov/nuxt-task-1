<template>
  <validation-observer v-slot="{handleSubmit}">
    <form class="validated-form"
      action="#"
      method="post"
      novalidate
      @submit.prevent="handleSubmit(onSubmit)"
    >
      <validated-field v-for="(fieldObj, index) of fieldObjects"
        :field-obj="fieldObj"
        :key="index"
        :index="index"
      >
      </validated-field>
      <validated-checkbox
        :checkbox-obj="checkboxObj">
      </validated-checkbox>
      <button class="validated-form__button" type="submit">
        <span class="validated-form__caption">
          Заполнить
        </span>
        <svg class="validated-form__icon">
          <?xml version="1.0" standalone="no"?>
          <!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
          <svg viewBox="0 0 10 10" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
            <line y2="9.903337" x2="0.090982" y1="1.539824" x1="8.454494" stroke-width="2"/>
            <line y2="0.570141" x2="9.424177" y1="1.418614" x1="8.575705" stroke-width="2"/>
          </svg>
        </svg>
      </button>
    </form>
  </validation-observer>
</template>

<script>
  import {ValidationObserver} from "vee-validate";
  import {extend} from "vee-validate";
  import {required, regex, email, oneOf} from "vee-validate/dist/rules";
  import {configure} from "vee-validate";

  extend('required', {
    ...required,
    message: 'Это поле обязательно для заполнения'
  });

  extend('regex', {
    ...regex,
    message: `{_field_} имеет неверный формат`,
  });

  extend('email', {
    ...email,
    message: `{_field_} имеет неверный формат`,
  });

  extend('oneOf', {
    ...oneOf,
    message: 'Необходимо принять пользовательское соглашение',
  });

  configure({
    classes: {
      valid: 'is-valid',
      invalid: 'is-invalid',
    }
  });

  export default {
    data() {
      return {
        isShow: false,
        fieldObjects: [
          {
            name: 'full-name',
            type: 'text',
            placeholder: 'ФИО',
            validationRules: {
              required: true,
              regex: /^([А-ЯЁA-Z][а-яёa-z]{1,14} ?){3}$/,
            },
          },
          {
            name: 'tel',
            type: 'tel',
            placeholder: 'Телефон',
            validationRules: {
              required: true,
              regex: /^(\+7)|8([- ]?\d{3}){2}([- ]?\d{2}){2}$/,
            },
          },
          {
            name: 'email',
            type: 'email',
            placeholder: 'Email',
            validationRules: {
              required: true,
              email: true,
            },
          },
          {
            name: 'note',
            type: 'text',
            placeholder: 'Примечание',
          },
        ],
        checkboxObj: {
          name: 'agree',
          caption: 'Пользовательское соглашение',
          isCaptionLink: true,
          validationRules: 'oneOf: 1'
        },
      }
    },
    methods: {
      onSubmit() {
        alert('Форма отправлена!');
      }
    },
    components: {
      ValidationObserver,
    },
  }
</script>