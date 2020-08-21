<template style="padding-right:0px;">

<div class="d-flex" style="padding-right:0px;">
<td style="padding-top:0px; padding-right:3px; width:280px; border-color:transparent;">
<p v-bind:style="text_style"> {{ textItem }}</p>
</td>

<form style="padding-right:4px; padding-left:0px; margin-left:0px;">
<button type="button" style="width: 97px; padding-left:9px;" v-bind:class="order_button_style" @click="on_order_button_click()">
{{ buttonText }}
</button>
</form>
</div>
</template>

<script>
export default {
  name: "FoodComponent",
  props: ['userId', 'item'], required: true,
    data() {
        return {
            item2: JSON.parse(this.item),
             isActive: true,
             error: null
        }
    },
  methods: {
    on_order_button_click() {
      this.item2.is_complete = !this.item2.is_complete;
    




 axios.post(
    '/profile/' + this.userId + '/' + this.item2.id,
    {is_complete : this.item2.is_complete}



  
 );



    }
    
  },
  
  computed: {
    buttonText() {
      return this.item2.is_complete === true ? "Completed" : "Complete";
    },

textItem() {

  return this.item2.title;

},

   order_button_style() {
      return this.item2.is_complete === true
        ? "btn btn-danger"
        : "btn btn-primary";
    },

       text_style() {
      return this.item2.is_complete === true
        ? "text-decoration: line-through;"
        : "text-decoration: none;";
    }
  
}

};




</script>