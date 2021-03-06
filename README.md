# things-alarm

## It prints the count of alarms in the form of badge and displays the list of alarms on the screen as a drop-down.

### It is used only by setting badge count from outside.
Example:

```html
    <things-alarm-badge
      count="10">
    </things-alarm-badge>
```

*****
</br></br>
### It provides the alarm from outside by message.
Example:

``` html
    <template is="dom-bind" id ="bind1">
      <things-alarm-badge align="center" id="alarm" messages="[[messages]]"></things-alarm-badge>
      <script type="text/javascript">
        document.getElementById('alarm').messages = [{
            title: 'message1',
            created_at: '2017-03-26 12:00:00',
            content: 'Test'
        }];
        document.getElementById('bind1').set('messages', [{
            title: 'message1',
            created_at: '2017-03-26 12:00:00',
            content: 'Test'
        }]);
      </script>
    </template>
```

*****
</br></br>
### Provide a message via iron-signal</br>
Subscribe event listener via iron-signal

```js
        this.fire('iron-signal',{name:'subscribed', data: message})
```

The object structure of message is as below.

```js
        {
            type: String, //badge,popup
            title: String,
            message: String
        }
```

[See iron-signals documentation](https://www.webcomponents.org/element/PolymerElements/iron-signals/)

Example:

```html
    <template is="dom-bind" id ="bind2">
      <paper-button onclick="onAddMessage()" raised> add messages</paper-button>
      <script type="text/javascript">
        function onAddMessage() {
            var msg = {
                type: 'badge',
                title: 'message1',
                created_at: '2017-03-26 12:00:00',
                content: 'Test'
            };
            document.getElementById('bind2').fire('iron-signal', {
                name: 'subscribed',
                data: {
                    message: msg
                }
            })
        }
      </script>
    </template>
```

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can
install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install

## Playing With Your Element

If you wish to work on your element in isolation, we recommend that you use
[Polyserve](https://github.com/PolymerLabs/polyserve) to keep your element's
bower dependencies in line. You can install it via:

    npm install -g polymer-cli

And you can run it via:

    polymer serve

Once running, you can preview your element at
`http://localhost:8080/components/things-alarm/`, where `things-alarm` is the name of the directory containing it.
