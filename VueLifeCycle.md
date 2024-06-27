## Vue Instance LifeCycle

![image](https://github.com/Vue-3-Learning/Vue3/assets/86046973/224902bb-2465-4730-b798-532cb6a0e5ab)

- beforeCreate: the 1st lifecycle hook that is reached is beforeCreated lifeCycle pahse followed by the created life cycle phase the only difference is that beforeCreate is called before the app is fully initialised whereas creayed is called thereafter at this point of time we still have nothing on the screen though after created vue just knows its data properties and is aware of general app configuration 
- created     ----|
-                 | ---now is the time when template is compiled so where all the dynamic placeholders, interpolations are removed and replaced by the concrete values taht should be shown to the users thereafter the beforeMount hook is reached
                   
- beforeMount ----| beforeMount means that this is right before the vue is actually going to bring something to the screen so right before we can see something 
- mounted: thats in the end just means that now we see something now vue app was initialised the template was compiled vue knows what to show on the screen and it handed those instructions of to the browser so that the browser really adds html elements with all the content we need as to find by our vue app 
- beforeUpdate: in vue apps data changes at some point of time and that then triggers a new lifecycle the update lifecycle hook , now we reach the before update and there after the updated hook this is a bit like before create and created beforeUpdate is reached before the update is really processed internally by vue 
- updated: updated is reached when it has been processed this btw also means that at this point of time the update is visible on the screen so we dont reached mounted again because the template was never unmounted so it always was visible afted updated chages just happend processed and have been rendered to the screen whereas in before update they havent 
- beforeUnmount: dometimes an instance can also been unmounted (all its conent is removed from the screen and the app is dead) you can use these lifecycle hooks to run any cleanup code you might wanna do
- unmounted
