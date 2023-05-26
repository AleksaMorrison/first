1.	How do you register a Vue component inside another component.?
 <parent>
    <childComp :some-value="someVale"></childComp>
 </parent>
 import childComp from './childComp.vue';

 export default {
    components: {
      ChildComponent
    },
    data() {
      return {
        someVale: 'Hello!'
      }
    }
  }

 2.	How can you use local storage with Vue.js?
 
 if localStorage() {
    localStorage.setItem(someData, this.input)
 }

 3.	How do you create an instance of Vue.js

 el: #appVue,
 data: {
    name: name,
    id: id,
    ...
 }

 4. How to create Two-Way Bindings in Vue.js?
 <v-model></v-model>=""
