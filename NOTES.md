
---
Already Finished the Basics 
Course: Vue - The Complete Guide (incl. Router & Composition API) by Maximilian Schwarzmüller
## Event Modifiers
-- For example you have a form and inside that you've a button and an input the problem is that (by default) when you click on the button it reloads the page..what if you want to handle this manually in vue or js so we use @click.prevent in <form> it is like event.preventDefault in js 
## v-once 
for example you have a situation in which you have to preserve the initial state i.e counter initial vlaue and after increment value ..v-once tell vue that any dynamic data binding should only be evaluated once 

## Data Binding + Event Binding
``` <input type="text" :value="name" @input="setName($event, lastName)">```
``` setName(event, lastName){this.name = event.input.value;} ```
``` resetInput(){this.name = ''}```
you can skip all this <input type="text" :value="name" @input="setName($event, lastName)"> by using v-modal <input type="text" v-modal="name"">

### What we know (thus far)
-  DOM interaction, templates and Data binding
-  Event Handeling 
