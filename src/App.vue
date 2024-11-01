<script setup lang="ts">
import { shallowRef, useTemplateRef } from 'vue';
import { DirectionalLight } from 'three';
import { TresCanvas } from '@tresjs/core';
import { OrbitControls } from '@tresjs/cientos';
import CustomCSS2DRenderer from './components/CustomCSS2DRenderer.vue';
import Label2D from './components/Label2D.vue';
const lightRef = shallowRef(new DirectionalLight());

setInterval(
  () => (lightRef.value.position.x = Math.sin(Date.now() * 0.01)),
  1000 / 60
);

const meshRef = useTemplateRef('mesh');
</script>

<template>
  <TresCanvas window-size clear-color="#82DBC5">
    <CustomCSS2DRenderer>
      <TresPerspectiveCamera :position="[9, 9, 9]" />
      <OrbitControls />
      <TresMesh ref="mesh" :position="[0, 0, 0]" cast-shadow>
        <TresBoxGeometry :args="[1.5, 1.5, 1.5]" />
        <TresMeshStandardMaterial />
      </TresMesh>
      <TresDirectionalLight
        ref="lightRef"
        :position="[-10, 10, 4]"
        :intensity="1.2"
        cast-shadow
      />
      <TresDirectionalLightHelper :args="[lightRef, 5]" />
      <Label2D :mesh="meshRef!"> Some Label </Label2D>
    </CustomCSS2DRenderer>
  </TresCanvas>
</template>
