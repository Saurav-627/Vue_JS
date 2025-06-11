<!-- Using Provide: (Full eg in App vue)
 
import { provide, reactive, ref } from "vue";

const maxNumber = ref(100);

provide("maxLuckyNumber", maxNumber);

this will pass the value of maxNumber to all the child components without prop drilling using unique key which is maxLuckyNumber.

Using Inject: (Full eg in LuckyNumber vue)
import { inject } from "vue";

const maxNumber = inject("maxLuckyNumber");

this is used to get the data from parent component note down always use a same key which is used in provide. -->
