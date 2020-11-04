<template>
  <f7-page name="product">
    <f7-navbar :title="product.title" back-link="Back"></f7-navbar>
    <f7-block-title>About {{product.title}}</f7-block-title>
    <f7-block strong>
      {{product.description}}
    </f7-block>
  </f7-page>
</template>
<script>
  import { store } from '../js/store';
  export default {
    props: {
      f7route: Object,
    },
    setup(props) {
      var productId = props.f7route.params.id;
      var currentProduct;
      store.state.products.forEach(function (product) {
        if (product.id === productId) {
          currentProduct = product;
        }
      });
      return {
        product: currentProduct,
      };
    }
  };
</script>
