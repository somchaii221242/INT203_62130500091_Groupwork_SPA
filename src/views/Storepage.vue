<template>
<div class="bg-red-100 min-h-screen">
  <div class="store">
    <store></store>
  </div>
  <div class="order">
    <order @confirm-order="confirmOrder" @edit-order="editOrder" @delete-order="deleteOrder" :sentItems="items" :sentOrderItems="orders"></order>
  </div>
</div>
</template>
<script>
import Store from '@/components/Storecomponent.vue'
import Order from '@/components/Ordercomponent.vue'

export default {
  name: 'storepage',
  components: {
    Store,Order
  },
  data(){
    return{
      url : 'http://localhost:5000',
      items : [],
      orders : [],
      count : {},
    }
  },
  methods:{
    async confirmOrder(item){
      try {
        const res = await fetch(this.url+"/order", {
          method: "POST",
          headers: {
            "content-type": "application/json",
          },
          body: JSON.stringify({
            id: ++this.count.runNumber,
            name : item.name,
            sweetness: item.sweetness,
          }),
        });
        const data = await res.json();
        this.orders = [...this.orders, data];
        this.runNumber();
      } catch (error) {
        console.log(`Could not save ! ${error}`);
      }
    },
    async runNumber(){
      try {
        const res = await fetch(`${this.url}/count`, {
          method: "PUT",
          headers:{
            'content-type' : 'application/json'
          },
          body: JSON.stringify({runNumber : this.count.runNumber})
        });
        this.count = await res.json();
      }
      catch (error) {
        console.log(`Could not save ! ${error}`);
      }
    },
    async editOrder(editingOrder){
      try {
        const res = await fetch(`${this.url}/order/${editingOrder.id}`, {
          method: "PUT",
          headers:{
            'content-type' : 'application/json'
          },
          body: JSON.stringify({id: editingOrder.id, name: editingOrder.name, sweetness: editingOrder.sweetness})
        });
        const data = await res.json();
        this.orders = this.orders.map(order => order.id == editingOrder.id ? {...order,name:data.name,sweetness:data.sweetness} : order);
    }
    catch (error) {
        console.log(`Could not edit ! ${error}`);
      }
    },
    async deleteOrder(deleteOrder){
      try {
        await fetch(`${this.url}/order/${deleteOrder.id}`, {
          method: "DELETE",
        });
        this.orders = this.orders.filter(
          (order) => order.id !== deleteOrder.id
        )
      } catch (error) {
        console.log(`Could not save ! ${error}`);
      }
    },
    async getOrderItems(){
      const res = await fetch(this.url+"/order");
      const data = await res.json();
      return data;
    },
    async getBeverageItems(){
      const res = await fetch(this.url+"/beverage");
      const data = await res.json();
      return data;
    }
  },
  async created(){
    this.items = await this.getBeverageItems();
    this.orders = await this.getOrderItems();
    const res = await fetch(this.url+"/count");
    this.count = await res.json();
  }
}
</script>