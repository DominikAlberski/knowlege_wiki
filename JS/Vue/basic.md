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

# computed properties

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

# v-model
allows to bind data from input into data property allowed for reactive actions

# methods
are trigger able and computed properties are based on reactivity
