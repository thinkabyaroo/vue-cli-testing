<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-4">
          <h1>hello</h1>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Itaque id delectus ab adipisci at eum, omnis nemo voluptas. Ducimus quas atque ullam itaque dolorum repellat deserunt modi magnam nulla quo?</p>
      </div>
    </div>
  </div>
    <div id="app" class="container">
        <div class="row my-5">
            <div class="col-lg-4 mx-5" >
                <h1 :class="{'text-danger':getTotal>5}">Fruit Lists: totoal({{ getTotal}})</h1>

                    <div class="row mb-3">
                        <div class="col-8">
                            <input type="text" v-model="newfruit">
                        </div>
                        <div class="col-4">
                            <button @click="addNewFruit">Add</button>
                        </div>
                    </div>
                    
                    <!-- <ul class="list-group">
                        <li class="list-group-item d-flex justify-content-between " v-for="(fruit,index) in fruits">
                            {{fruit}}
                            <div>
                                <button  class="btn btn-sm btn-info" @click="edit(index)">Edit</button>
                                <button  class="btn btn-sm btn-danger" @click="del(fruit)">Delete</button>
                            </div>
                        </li>
                    </ul> -->
            </div>

            <div class="col-lg-4 mx-5">
              <h3>Voucher:{{vId}}</h3>
              <form action="" @submit.prevent="saveItem">
              <div class="row">
                <div class="col">
                  <label for="" class="form-label">Select item</label>
                  <select class="form-select form-select-lg" v-model="selectedItem" id="" aria-label="Default select example">
                    <option v-for="item in items" :value="item.id" :key="item.name">{{item.name}}</option>
                  </select>
                </div>
                <div class="col">
                  <label for="" class="form-label">quality</label>
                  <input type="number" class="form-control form-control-lg" v-model="inputQuantity" id="" >
                </div>
                <div class="col">
                  <button  class="btn btn-primary">Add Item</button>
                </div>
              </div>
                
              </form>
           
            </div>
            <div class="col-lg-8">
               <table class="table table-bordered my-3">
                <thead>
                  <tr>
                    <th>#</th>
                    <th>Item</th>
                    <th>quantity</th>
                    <th>Cost</th>
                    <th></th>
                  </tr>

                </thead>
                <tbody>
                  <tr>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                  </tr>

                </tbody>
               </table>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    data() {
      return{
                    count:1,
                    name:'thin kabyar',
                    fruits:['apple','aaa','bbb','orange','banana'],
                    newfruit:"",
                    vId:(Math.random()*10000).toFixed(0),
                    selectItem:null,
                    inputQuantity:null,
                    lists:[],

                    items:[
                      {
                        id:1,
                        name:"apple",
                        price:"50",
                      },
                       {
                        id:2,
                        name:"orange",
                        price:"150",
                      },
                       {
                        id:3,
                        name:"banana",
                        price:"40",
                      },
                       {
                        id:4,
                        name:"mango",
                        price:"50",
                      },
                    ]
                }
    },
    computed: {
      getTotal(){
                    return this.fruits.length
                },
      name(){
        return this.data
      }
    },
    methods: {
    //  addNewFruit(){
    //                 // alert("hello")
    //                 this.fruits.push(this.newfruit)
    //                 this.newfruit=""
    //             },
    //             del(x){
    //                 // if(confirm("R U sure to delete")){
    //                 //     this.fruits=this.fruits.filter(fruit=>fruit!=x)

    //                 // }
    //                 v.fruits.splice(x,1)
    //             },
    //             edit(x){
    //                 let newVel=prompt("do u want to edit",this.fruits[x]);
    //                 this.fruits[x]=newVel;
    //             }

    saveItem(){
      // alert("hello")
      let list={
        itemId : this.selectedItem,
        quantity : this.inputQuantity,
        unitPrice : this.item.find(el=>el.id === this.selectedItem).price,
        cost : this.items.find(el=>el.id===this.selectedItem).price* this.inputQuantity
      }
      this.selectedItem=null;
      this.inputQuantity=null;
      this.lists.push(list)
    }
    },
    

  }
  
</script>

<style lang="scss" scoped>

</style>
