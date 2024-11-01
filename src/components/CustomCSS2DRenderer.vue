<script setup lang="ts">
import { CSS2DRenderer } from 'three/addons/renderers/CSS2DRenderer.js';

const labelRenderer = new CSS2DRenderer();
labelRenderer.setSize(window.innerWidth, window.innerHeight);
labelRenderer.domElement.style.position = 'absolute';
labelRenderer.domElement.style.top = '0px';
labelRenderer.domElement.style['pointer-events'] = 'none';
document.body.appendChild(labelRenderer.domElement);
</script>

<template>
  <slot />
</template>
