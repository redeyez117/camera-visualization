<template>
<div v-bind="$attrs" :style="position" class="camera">
  <slot></slot>
</div>

</template>

<script>
export default {
  name: "Camera",
  props: ['position']
}
</script>

<style scoped>
.camera {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  background: #282828;
  position: absolute;
  transform-style: preserve-3d;
  z-index:5;
  cursor: pointer;
}

.camera::after {
  content: "";
  position: absolute;
  display: none;
  width: 10px;
  height: 18px;
  border-bottom: 500px solid rgba(255, 255, 255, .6);
  border-left: 250px solid transparent;
  border-right: 250px solid transparent;
  z-index: 5;
  top: 49%;
  transform: translateZ(-1px);
}

.camera:hover{
  background: grey !important;
}

.camera:hover.camera:after {
  display: block;
}
</style>