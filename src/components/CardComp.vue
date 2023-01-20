<template>
  <div class="card">
    <h6 class="titleWarn">Тут должна было быть картинка, но мою карту API не принимает</h6>
    <div v-if="palce?.address.state" class="wrapperText">
      <strong>state:</strong>
      <p>{{ palce?.address.state }}</p>
    </div>
    <div v-if="palce.address.state" class="wrapperText">
      <strong>country:</strong>
      <p>{{ palce.address.country }}</p>
    </div>
    <div v-if="palce.address.state" class="wrapperText">
      <strong>state:</strong>
      <p>{{ palce.address.state }}</p>
    </div>
  </div>
</template>

<script  lang="ts">
import { PropType } from 'vue';
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
    palce: Object as PropType<palceType>
  }
})
export default class CardComp extends Vue {
  palce!: palceType
}
type palceType = {
  place_id: number;
  licence: string;
  osm_type: string;
  osm_id: number;
  boundingbox: string[];
  lat: string;
  lon: string;
  display_name: string;
  class: string;
  type: string;
  importance: number;
  icon: string;
  address: Address;
}

type Address = {
  hamlet: string;
  county: string;
  state: string;
  'ISO3166-2-lvl4': string;
  country: string;
  country_code: string;
}
</script>

<style lang="scss" scoped>
.card {
  flex: 1 1 33%;
  width: 33%;
  max-width: 33%;
  padding: 0px 8px;
  margin-bottom: 16px;
  border: 3px solid rgb(49, 47, 199);
  margin: 10px;
  padding: 10px;

  img {
    width: 100%;
    height: 300px;
    object-fit: cover;
    border-radius: 16px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);
    transition: 0.4s;
  }

  .titleWarn {
    text-align: center;
  }

  .wrapperText {
    margin-top: 10px;
    display: flex;
    text-align: center;

    p {
      margin-left: 10px;
    }
  }

  h3 {
    padding: 16px;
    color: #313131;
    transition: 0.4s;
  }

  &:hover {
    img {
      transform: scale(1.05);
    }

    h3 {
      color: #24c444;
    }
  }
}
</style>