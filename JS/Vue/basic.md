`{{}}` - allows to render anything that is in data object
to bind smg to attribute use `v-bind:title` or in shorthand just `:`

Basic app structure:

```vue
  <body>
    <div id="app">
        <h1>{{ tittle }}</h1>
        <a :href="link">{{linkTitle}}
    </div>

    <script>
        var app = new Vue({
            el: '#app',
            data: {
                title: 'Learning Vue on Scrimba',
                link: 'http://exampl.com',
                linkTitle: 'link title'
            }
        });
    </script>
  </body>
```

### computed properties

```vue
data: {
          message: 'Learning Vue'
      },
computed: {
              exclamation: function() {
                  return this.message + '!!!';
              }
          }
```
computed properties could be set as objects with set: and get keys so the would
act accordingly if the action is setting or getting the value

`v-model` - allows to bind data from input into data property allowed for reactive actions

### methods
are trigger able and computed properties are based on reactivity

`v-once` - updates value only once
`v-html="[...]"` - allows to output html: `<div><p>some text</p></div>`
`v-text="[...]"` - the same thing as `{{ }}`

`<template>` - special vue syntax tag for grouping markup together without adding anything to DOM structure

`v-if="[...]"` - first condition render if true
`v-else-if="[...]"` - second condition
`v-else`       - default
this physically remove components from DOM

object based class binding sytnax
`v-bind:class="{ 'css-class-name': vueDataAttr }"` - allows to bind class attribute with data

array based class binding syntax
`v-bind:class="[vueDataAttr]" || v-bind:class="[vueDataAttr ? attrWithOnecClass : attrWithSecondClass]"` - allows direct bind of data attributes to classes

You can combine object with array based notation
`v-bind:class="[{css-class-name: vueDataAttr}, otherDataAttr]"`

### Components

#### Component defined within main Vue app

```vue
  <first-component user-id="123"> # for component to accept data like this it need to be in kebab-case which further down should be reference as UserID in CamelCase. Vue will automatically convert passed JSON string into object if we precede name of prop in template with v-bind: or simple :
    <template v-slot:mySlotName>
      This will not be renderd unless in template there would be
      <slot name="mySlotName">{{ message }}</slot>
    </template>
  </first-component>

Vue.component('first-component', {
  template: '<div> this will be displayed as in first-component tag with {{ message }} <slot name="mySlotName"></slot></div>',

  props: ['userID'] #
  data: function() {
    return { message: 'some message'}
  } # this is main diff from data in components you need function returning object
});
```
#### Single File Component SFC

```vue
import MyComponent from './path/to/component' # path/to/component.vue

Vue.component('my-component', MyComponent)

new Vue({
  el: '#app',

  # as alternative to Vue.component we can use other syntax to register locally:
  # components: { MyComponent }

  data: {
    message: 'test'
  }
});

# inside path/to/component.vue

<template>
  <div>
    <p> Hello from component {{ test }} </p>
    <inside-component/>
  </div> # SINGLE WRAPPING TAG!!!

  <div> </div> # This will fail
</template>

<script>
  const InsideComponent = require('./InsideComponent') # component in other component

  module.exports = {
    components: {
      InsideComponent
    },

    data: function() {
      return { test: 'Test message' }
    }
  }
</script>

<style scoped> # when scoped is used style definitions are scoped to component
</style>
```

###### Props

```vue
# in html:
<props title="Title for my props" :is-published="false" :views="123", :post="post"
# v-bind="post" binds object properties that can be accepted singularly inside components props />

# in component:
  props: {
    title: String,
    control: {
      type: [Boolean, Number],
      default: false # this way when prop isn't passed thru we still have default
    }
    counter: Number,
    post: Object
  }
```

### EVENTS
` v-on:[EVENT_TYPE].[Modifier]="[ACTION]" `
` v-on == @ `
Common event types
  * click
  * submit
  * keyup - needs pair with specific key as modifier
  <!-- keyup.escape="someFunciton" -->
  * custom event

Modifiers:
  * prevent - prevents default event action
  <!-- v-on:click.prevent="someFunction" -->
  * once - lets action happen once

#### custom events
Application specific event
They are the only way to communicate from child to parent component

exp:
child:
  $emit('my-event', only_one_optional_parameter)
parent:
  v-on:my-event="myFunction($event)"





