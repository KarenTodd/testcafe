```js
{
    modifiers: {
        ctrl: Boolean,
        alt: Boolean,
        shift: Boolean,
        meta: Boolean
    },

    offsetX: Number,
    offsetY: Number,
    caretPos: Number,
    replace: Boolean,
    paste: Boolean,
    speed: Number
}
```

Parameter                      | Type    | Description                                                                                                                                           | Default
------------------------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------
`ctrl`, `alt`, `shift`, `meta` | Boolean | Indicates which modifier keys should be pressed while typing.                                                                                          | `false`
`offsetX`, `offsetY`           | Number  | Mouse pointer coordinates that define a point where the action is performed or started. If an offset is a positive integer, coordinates are calculated relative to the top-left corner of the target element. If an offset is a negative integer, they are calculated relative to the bottom-right corner. | The center of the target element.
`caretPos`                     | Number  | The initial caret position. A zero-based integer.                                                                                        | The length of the input field content.
`replace`                      | Boolean | `true` to remove the text in the target element, and `false` to leave the text as it is.                                                         | `false`
`paste`                        | Boolean | `true` to insert the text in a single keystroke (similar to a copy & paste function), and `false` to insert the text character by character.                         | `false`
`speed`   | Number | The speed of action emulation. Defines how fast TestCafe performs the action when running tests. A number between `1` (the maximum speed) and `0.01` (the minimum speed). If test speed is also specified in the [CLI](/testcafe/documentation/reference/command-line-interface.html#--speed-factor), [API](/testcafe/documentation/reference/testcafe-api/runner/run.html) or in [test code](/testcafe/documentation/reference/test-api/testcontroller/settestspeed.html), the action speed setting overrides test speed. | `1`

**Example**

```js
import { Selector } from 'testcafe';

const nameInput = Selector('#developer-name');

fixture `My Fixture`
    .page `http://devexpress.github.io/testcafe/example/`

test('My Test', async t => {
    await t
        .typeText(nameInput, 'Peter')
        .typeText(nameInput, 'Parker', { replace: true });
});
```
