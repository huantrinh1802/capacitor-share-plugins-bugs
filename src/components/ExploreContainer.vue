<template>
  <div id="container">
    <strong>{{ name }}</strong>
    <p>Explore 
      <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI
        Components
      </a>
    </p>
    <IonButton @click="shareTheCode">Share</IonButton>
  </div>
</template>

<script setup lang="ts">
import { Share } from '@capacitor/share';
import { IonButton } from '@ionic/vue';
import { ref } from 'vue';
defineProps({
  name: String,
});
const url = ref('https://www.humaniti.com/referral/?ftName=john&signupCode=923')
const shareObj = {
  title: 'Share this',
  text: 'But also share that',
  url: url.value
}
async function shareTheCode() {
  
    await Share.share(shareObj).then(() => console.log('Successfully share')).catch(() => {
      console.log('Share is cancelled');
    });
}
</script>
<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
