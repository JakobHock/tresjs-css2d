<script setup lang="ts">
import * as THREE from "three"
import {onMounted, useTemplateRef} from "vue"

import { CSS2DObject } from 'three/addons/renderers/CSS2DRenderer.js';

type Props {
  mesh: THREE.Mesh
}
const props = defineProps<Props>()

const labeldiv = useTemplateRef("labeldiv")

onMounted(() => {
  const label = new CSS2DObject( labeldiv );
	label.center.set( 0, 0 );
	mesh.add( label );
	label.layers.set( 1 );
})
</script>

<template>
  <div ref="labeldiv">
    <slot />
  </div>
</template>
