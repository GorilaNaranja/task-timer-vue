<template>
  <div class="creator-box">
    <p> We have {{ tasks.length }} tasks running </p>
  </div>
</template>

<script>
export default {
  props: ["tasks"]
};
</script>
