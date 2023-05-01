<template>
  <div class="home">
    <h1>DropZone</h1>    
     <DropZone @drop.prevent="drop" @change="selectedFile" />
     <span class="file-info">File: {{dropZoneFile.name}}</span>
  </div>
</template>

<script>
// @ is an alias to /src
import DropZone from '@/components/DropZone.vue';
import {ref} from "vue";

export default {
  name: 'HomeView',
  components: {
    DropZone
  },
  setup() {
    let dropZoneFile = ref("");

    const drop = (event) => {
      dropZoneFile.value = event.dataTransfer.files[0];
    };

    const selectedFile = () => {
      dropZoneFile.value = document.querySelector(".dropZoneFile").files[0];
    };

    return { dropZoneFile, drop, selectedFile };
  },
};
</script>

<style lang="scss" scoped>
.home {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;
  h1 {
    font-size: 40px;
    margin-bottom: 32px;
  }
  .file-info {
    margin-top: 32px;
  }
}
</style>