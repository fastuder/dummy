<template>
  <div class="quote">
    <h1>{{ firstName }}</h1>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class Quote extends Vue {
  @Prop() id!: number;
  @Prop() imageUrl!: string;
  @Prop() firstName!: string;
  @Prop() lastName!: string;
  @Prop() email!: string;
  @Prop() contactNumber!: string;
  @Prop() age!: number;
  @Prop() dob!: string;
  @Prop() salary!: number;
  @Prop() address!: string;
}
</script>