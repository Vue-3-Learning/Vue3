- [Event Modifiers](#event-modifiers)
- [Computed Properties](#computed-properties)
- [watchers](#watchers)
- [Data Binding and Event Binding](#data-binding-and-event-binding)
- [class binding](#class-binding)
- [Refs](#refs)
- [Node JS](#node-js)
- [Components](#components)
- [Emitting Events](#emitting-events)
- [Provide and Inject](#provide-and-inject)
- [Slots](#slots)
- [Teleporting](#teleporting)
---
Already Finished the Basics 
Course: Vue - The Complete Guide (incl. Router & Composition API) by Maximilian Schwarzmüller
## Event Modifiers
-- For example you have a form and inside that you've a button and an input the problem is that (by default) when you click on the button it reloads the page..what if you want to handle this manually in vue or js so we use @click.prevent in <form> it is like event.preventDefault in js 
## v-once 
for example you have a situation in which you have to preserve the initial state i.e counter initial vlaue and after increment value ..v-once tell vue that any dynamic data binding should only be evaluated once 

## Data Binding and Event Binding
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

  ## Vue Reactivity
  - vue keeps track of data that is defined in data(){} it take all the properties defined there and merge them in a global behind the scene object the same object where your methods are merged
  - when it comes to data the important key thing vue does is change your data object into a reactive data object by escentialy wrapping your properties with js faeture called proxy
 ## Refs
 - vue has a feature that allow us to retrieve values from dom elements when you need them instead all the time (like in v-model or event.target.vlaue we retrieve with each kay stroke) and taht feature is called refs
 - <input type="text" ref="userText"
 - why am i doing this ? coz vue detects such refs and stores them internally , it bascially memorises that you need access to that element
 - ``` setTxt(){ //instead of this.message = event.target.value ; this.message = this.$refs.userText //this points to the element //refs is a object full of key value pairs where the key is the ref identifier we defined in ele we access its value by .value}```

## How Vue Updates the DOM
![image](https://github.com/Vue-3-Learning/Vue3/assets/86046973/5b10bfaa-4a1f-43f4-a2d9-c35e52051cff)

- all vue instructions are removed from the dom when its template is rendered in the dom

## Node JS
node js is a js runtimewhich allows to run javascript outside the browser, you could use js to write server side code using js 
## Components
![image](https://github.com/Vue-3-Learning/Vue3/assets/86046973/fa195555-d4f6-4a24-9cf8-a56666bc8acd)

## Emitting Events

- to communicate from child to parent
- this.$emit()
- this.$emit('toggle-friend') ... toggle-friend method name..you can pass as many argument as you want and every extra argument will simply be the data that you pass together with your data this.$emit('toggle-friend', this.id) and that will then provided as a first argument to the method that listens to this event 
- in parent we'll listen to it @toggle-friend="toggleFav"
  ### custom events
  you van add validation and can register the emits as props[not required but recommended] like emits:['name-of-event'] or

  ``` emits:{ ```
 ```'name-of-event': function(id){ if(id){return true} ```
``` } ```
 ``` } ```

## Provide and Inject
- a pattern you can use to provide data in one place and inject it which means use it in another place 
- provide{ data you want to provide}
 we also neew to listen to this provided data
- in the component you want to use the data ...we add inject method ..inject basically works as props inject:['data-name']
- you can only inject what has been provided on a higher up level which means in a parent or ansestor component   
- to avoid duplicate code i.e the property defined in provide as well as data
- ``` provide() ```
- ```return { ```
- ``` topics: this.topics }```
- ```}```
## Slots
- we can pass dynamic content between the opening and closing tags of a component
```
<template>
    <section>
        <div>
            <slot></slot>
        </div>
    </section>
</template>
<script>
export default{

}
</script>
<style scoped>
 section {
    margin: 2rem auto;
    max-width: 30rem;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    padding: 1rem;
  }
  
  section div {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>

the other component 
<template>
    <section>
      <base-card>
      <h2>Available Badges</h2>
      <ul>
        <li>
          <base-badge type="admin" caption="ADMIN"></base-badge>
        </li>
        <li>
          <base-badge type="author" caption="AUTHOR"></base-badge>
        </li>
      </ul>
    </base-card>
    </section>
  </template>
```
but sometimes you have a scenario when your custom component has lots of slots for example in our case we have only one slot <slot></slot> but it is not unrealistic that we have more than one ..here named slots come into play 
- you dont have to name all slots but the unnamed slot will be the default slot and there should be only one unnamed slot ...and now you can assign the content to different slots
```
 <section>
        <header>
            <slot name="header"></slot>
        </header>
        <div>
            <slot></slot>
        </div>
    </section>
```
and in other component 
```
<section>
      <base-card>
      <template v-slot:header>
        <h3>{{ fullName }}</h3>
        <base-badge :type="role" :caption="role.toUpperCase()"></base-badge>
      </template>
      <p>{{ infoText }}</p>
    </base-card>
    </section>
```
- $slots.slotname
- shorthand #slotname instead of v-slot:
  ### scoped slots
  - we only have access to whatever exists in the app scope so the goal is in one scope to access it in other we will use scoped slots
  ```
  <li v-for="goal in goals" :key="goal">
  <slot :item="goal"></slot>
  </li>
  ```
in the component where we're using it
```
<base-card>
<template #default="slotProps">
<p>{{slotProps.item}}</p>
</template>
</base-card>
```
## Dynamic Component
```
   <button @click="setSelected(active-goals)"> //active-goals componnt name
            Active Goal
        </button>
        <button @click="setSelected((manage-goals))">
            Manage Goal
        </button>
        <component :is="selectedComponent"></component> //selectedComponent component name
```
### Keep Alive dynamic components
in our example lets suppose you have a input filed in manage goals component and you  type something in it and without saving it you clicked on the other tab all data will lost because when you chnage tab the other component get destroyed here <keep-alive> come into play
```
<keep-alive> <component :is="selectedComponent"></component></keep-alive>
```
keep alive allows you to tell vue that components should not be removed and deleted entirely but instead their state should be saved and they should be cached 
 ## Teleporting
 ```
 <teleport to="#app">
       <h2>Available Badges</h2>
      <ul>
        <li>
          <base-badge type="admin" caption="ADMIN"></base-badge>
        </li>
        <li>
          <base-badge type="author" caption="AUTHOR"></base-badge>
        </li>
      </ul>
 </teleport>
```
teleport wants one attribute the to prop and here you provide a css selector selecting an html element on your entire page where this content should actually be added to in the html markup so logically it still belongs to the component in which it is written you can still interact with methods but it will be rendered somewhere lese in the dom structure you can also refer to the tag i.e to="body" it means please render it in the body element directly and not deeply nested in this html structure

![image](https://github.com/Vue-3-Learning/Vue3/assets/86046973/11607c83-90e6-4e87-bdbc-20f67eb444c0)

