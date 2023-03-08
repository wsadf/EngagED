<template>
<InternaMain>
  <ListCharacter />
</InternaMain>
</template>

<script>
import InternaMain from '@/components/InternaMain.vue';
import ListCharacter from '@/components/ListCharacter.vue';


export default {
  name: 'HomeView',
  components: {
    InternaMain,
    ListCharacter
  }
}
</script>
