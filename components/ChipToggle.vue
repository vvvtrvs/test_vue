<template>
  <div style="position:relative;">
    <label class="switch">
      <input
        type="checkbox"
        :value="value"
        @change="$emit('input', $event.target.checked)"
      />
      <span class="slider"> </span>
    </label>
    <span
      :class="[
        !value ? 'white--text' : 'grey--text',
        'overline',
        'font-weight-medium',
        'label',
        'positive'
      ]"
      >{{ positiveText }}</span
    >
    <span
      :class="[
        value ? 'white--text' : 'grey--text',
        'overline',
        'font-weight-medium',
        'label',
        'negative'
      ]"
      >{{ negativeText }}</span
    >
  </div>
</template>

<script>
export default {
  props: { positiveText: String, negativeText: String, value: Boolean }
};
</script>

<style>
/* The switch - the box around the slider */
.switch {
  position: relative;
  display: inline-block;
  width: 90px;
  height: 40px;
}

/* Hide default HTML checkbox */
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

/* The slider */
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 40px;
  background-color: #eee;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  border-radius: 40px;
  position: absolute;
  content: "";
  height: 40px;
  width: 52px;
  background-color: black;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider:before {
  -webkit-transform: translateX(38px);
  -ms-transform: translateX(38px);
  transform: translateX(38px);
}

.label {
  pointer-events: none;
  position: absolute;
  top: 4px;
}
.label.positive {
  left: 20px;
}
.label.negative {
  right: 16px;
}
</style>
