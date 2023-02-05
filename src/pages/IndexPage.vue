<template>
  <q-page class="row items-center justify-evenly">
    <example-component
      title="Example component"
      active
      :todos="todos"
      :meta="meta"
      :products="products"
    ></example-component>
    <calculator-component></calculator-component>
  </q-page>
</template>

<script lang="ts">
import { Todo, Meta } from 'components/models';
import { Product } from 'components/models';
import ExampleComponent from 'components/ExampleComponent.vue';
import CalculatorComponent from 'components/CalculatorComponent.vue';
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'IndexPage',
  components: { ExampleComponent, CalculatorComponent },
  setup() {
    const products = ref<Product[]>([
      {
        id: 'NK001',
        title: 'Nasi Katok',
        description:
          'Small portion of Chicken Rice for 1 pax with hot belacan sauce',
        price: 1.5,
        quantity: 10,
        image: 'http://placekitten.com/200/300',
      },
      {
        id: 'NK001',
        title: 'Nasi Katok',
        description:
          'Small portion of Chicken Rice for 1 pax with hot belacan sauce',
        price: 1.5,
        quantity: 10,
        image: 'http://placekitten.com/200/300',
      },
      {
        id: 'NK001',
        title: 'Nasi Katok',
        description:
          'Small portion of Chicken Rice for 1 pax with hot belacan sauce',
        price: 1.5,
        quantity: 10,
        image: 'http://placekitten.com/200/300',
      },
      {
        id: 'NK001',
        title: 'Nasi Katok',
        description:
          'Small portion of Chicken Rice for 1 pax with hot belacan sauce',
        price: 1.5,
        quantity: 10,
        image: 'http://placekitten.com/200/300',
      },
    ]);
    const todos = ref<Todo[]>([
      {
        id: 1,
        content: 'ct1',
      },
      {
        id: 2,
        content: 'ct2',
      },
      {
        id: 3,
        content: 'ct3',
      },
      {
        id: 4,
        content: 'ct4',
      },
      {
        id: 5,
        content: 'ct5',
      },
    ]);
    const meta = ref<Meta>({
      totalCount: 1200,
    });
    return { todos, meta, products };
  },
});
</script>
