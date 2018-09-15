<template>
  <div>
    <b-container>
      <form @submit.prevent="onSubmit">
        <h2>Products list</h2>
        <ul>
          <li v-for="(product, index) in products" :key="product.id">
            {{ product.name }} <b-button variant="danger" @click="removeProduct(index)">remove product</b-button>
          </li>
        </ul>
        <p v-if="!products.length">No products!</p>
        <b-input name="name" v-validate="'required|min:3'" @keyup.enter="onSubmit()" type="text" v-model="name" />
        <div v-show="errors.has('name')">
          {{ errors.first('name') }}
        </div>
        <b-button variant="success" @click="onSubmit()">Add product</b-button>
      </form>

    </b-container>
  </div>
</template>

<script>
    import uuid from 'uuid/v4';

    export default {
      name: 'MyForm',
      data(){
        return {
            name: '',
            products: [{
                id: 0,
                name: 'Coś'
            }, {
                id: 1,
                name: 'Coś2'
            }]
        }
      },
      methods: {
          addProduct(){
              this.products.push(
                  {
                      id: uuid,
                      name: this.name
                  }
              )
              this.name = '';
              this.$validator.reset();
          },
          removeProduct(index){
              this.products.splice(index, 1);
          },
          onSubmit() {
              this.$validator.validateAll().then(result => {
                  if (!result) {
                      return;
                  }
                  this.addProduct();
              });
          }
      }
  }
</script>

<style lang="scss" scoped>
  ul{
    list-style: none;
    padding: 0;
  }
  li{
    padding: 15px 0;
    border-bottom: 1px #eaeaea solid;
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
</style>
