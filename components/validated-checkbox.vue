<template>
  <validation-provider
    :rules="checkboxObj.validationRules"
    v-slot="{classes, errors}"
    tag="div"
  >
    <label class="validated-form__checkbox"
      :class="classes"
    >
      <div class="validated-form__screed validated-form__screed--checkbox">
        <input class="validated-form__input"
          v-model="value"
          type="checkbox"
          :id="checkboxObj.name"
          :name="checkboxObj.name"
        >
        <svg class="validated-form__icon validated-form__icon--checkbox">
          <?xml version="1.0" standalone="no"?>
          <!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
          <svg viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
          >
            <rect width="100%" height="100%"/>
            <line class="validated-form__check-border"
              x1="0.75" y1="0.75" x2="19.25" y2="0.75" stroke-width="1.5"/>
            <line class="validated-form__check-border"
              x1="0.75" y1="19.25" x2="19.25" y2="19.25" stroke-width="1.5"/>
            <line class="validated-form__check-border"
              x1="0.75" y1="0.75" x2="0.75" y2="19.25" stroke-width="1.5"/>
            <line class="validated-form__check-border"
              x1="19.25" y1="0.75" x2="20" y2="19.25" stroke-width="1.5"/>
            <line class="validated-form__check-mark"
              x1="4.057992" y1="8.971923" x2="9.565218" y2="14" stroke-width="1.5"
            />
            <line class="validated-form__check-mark"
              x1="8.575" y1="14" x2="16.521714" y2="4.913967" stroke-width="1.5"
            />
          </svg>
        </svg>
        <a class="validated-form__caption" href="#">
          {{checkboxObj.caption}}
        </a>
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
        value: false,
      }
    },
    props: {
      'checkbox-obj': Object,
    },
    components: {
      ValidationProvider,
    },
  }
</script>