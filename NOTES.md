
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

## computed properties
- these are like methods but with one difference vue will know about their depenencies and will only re-excecute if one of the dependency changes 
- only use methods when you know that you have to recalculate a value everytime anything on the page change but you still bind your events to the methods not the computed properties you really use computed properties for outputing something 

## watchers
- it is bascially a function you tell vue to execute only when one of its dependencies changes
for example you have a name data property and a watcher of that name() every time the name property changes the name() fun re-execute 
- we dont return anything in it instead we write logic we want to execute on that property change 
- name(value) .. vue automatically pass the last value of the property to the watcher, we also can pass a second argument which would be the old value of the property
- we can use it as a computed property but we would have couple of problems in that case for example what if a data property is beign calculated by 2 or 3 dependencies? then we've to make watcher for each that a lot of code
- use for any non-data update you want to make
## class binding

- :class="addClass? 'red' : 'black'" 
- :class="{demo: true, newClass: addClass}" //add demo every time and newClass only when addClass is true


