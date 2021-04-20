<template>

    <div>
      <div class="bg-red-500 text-center">
        <h1>Order Form</h1>
        <form @submit.prevent="confirmOrder">
          <div>
            <label for="name">Name : </label>
            <select name="name" v-model="chosenItem">
              <option v-for="item in sentItems" :key="item.id" :value="item.name">
                {{item.name}}
              </option>
            </select>
            </div>
            <label for="sweetness">Sweetness : </label>
          <div id="sweetness">
            <label for="100-sweetness">100 % : </label> 
            <input type="radio" id="100-sweetness" v-model="chosenSweetness" value="100"/>
          </div>
          <div>
            <label for="75-sweetness">75 % : </label> 
            <input type="radio" id="75-sweetness" v-model="chosenSweetness" value="75"/>
          </div>
          <div>
            <label for="50-sweetness">50 % : </label> 
            <input type="radio" id="50-sweetness" v-model="chosenSweetness" value="50" />
          </div>
          <div>
            <label for="25-sweetness">25 % : </label> 
            <input type="radio" id="25-sweetness" v-model="chosenSweetness" value="25"/>
          </div>
          <div>
            <label for="0-sweetness">0 % : </label> 
            <input type="radio" id="0-sweetness" v-model="chosenSweetness" value="0"/>
          </div>
          <button type="submit" class="bg-yellow-100  border-2 px-2 py-1 text-m font-semibold">Confirm</button>
        </form>
      </div>
      
      <div v-if="this.sentOrderItems">
        <h1>Order Details</h1>
        <ul>
          <li v-for="order in sentOrderItems" :key="order.id">
            Order number #<span>{{order.id}}</span>&nbsp;name:&nbsp;<span>{{order.name}}</span>
            &nbsp;Sweetness: &nbsp;<span>{{order.sweetness}}</span>
            <span><button @click="editOrder(order)">&nbsp;edit&nbsp;</button></span>
            <span><button @click="deleteOrder(order)">delete</button></span>
          </li>
        </ul>
      </div>

    </div>
</template>

<script>
export default {
  name: "Order",
  props: {
    sentItems : Array, sentOrderItems : Array
  },
  emits: ["confirm-order","edit-order","delete-order"],
  data(){
    return{
      editingId : null,
      chosenItem : null,
      chosenSweetness : null,
      isEdit : false,
    }
  },
  methods:{
    confirmOrder(){
      if(this.isEdit){
        this.$emit('edit-order',{id : this.editingId, name:this.chosenItem,sweetness : this.chosenSweetness});
        this.editingId = null;
        this.chosenItem = null;
        this.chosenSweetness = null;
        this.isEdit = false;
      }
      else{
      this.$emit('confirm-order',{name :this.chosenItem, sweetness :this.chosenSweetness});
      }
    },
    editOrder(order){
      this.isEdit = true;
      this.editingId = order.id;
      this.chosenItem = order.name;
      this.chosenSweetness = order.sweetness;
    },
    deleteOrder(order){
      this.$emit('delete-order',order);
    }
  }
};
</script>
