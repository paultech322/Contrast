<script setup lang="ts">  
  const props = defineProps(['modelValue', 'hint']);
  const emit = defineEmits(['update:modelValue']);
  
  const onChange = (ev: Event) => {
    emit('update:modelValue', (ev.target as HTMLInputElement).value)  
  }
  
  const onFocus = (ev: Event) => {
    (ev.target as HTMLInputElement).select()
  }
</script>

<template>
  <input
    :aria-label="props.hint"
    type="text" 
    :value="modelValue"
    @change="onChange($event)"
    @focus="onFocus($event)" 
  />
</template>

<style scoped>
  input {
    appearance: none;
    border: none;
    background: transparent;
    color: var(--text-color);
    
    border: 1px solid transparent;
    
    border-radius: 4px;
    
    padding: 0px 16px;
    
    text-transform: uppercase;
    
    width: 100px;  
    
    font-size: 1rem;  
    font-family: inherit;
  }
  
  @media (any-hover: hover) {
    input:hover {
      border: 1px solid var(--border-color);
    }
  }
  
  input:focus-visible {
    outline: 1px solid var(--border-color);
  }
</style>