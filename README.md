# serenix_readonly.js

> Make form controls - even `<select>` - read-only. Elements made read-only, remains focusable: **they are not disabled**.

## About

On July 2021, when developping UI field and form in javascript, I needed to set 'read-only' not 'disabled' some elements of a form. Facing the inconsistency of 'readonly' attribute on input an 'select' element, I started to find on internet an existing solution. I finally found Readonly.js library of Arthur Corenzan. I was not able to make all input element non editable with that library and I decided to write this library (**serenix_readonly.js**).
**serenix_readonly.js** is a lightweight library to fix the inconsistency of the `readonly` attribute in form controls. According to [current specifications](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#attr-readonly) the attribute will be ignored in certain input types, and is completely void in `<select>` elements. This little helper aims to fix that. If you're curious to know more read the [Web Standards](#web-standards) section.
The read-only state is guaranteed by a change listener that is added when the read-only state argument value is true and removed when the state argument is false. 

This version is not minified and used for indentation, four spaces instead of tabultation character. This can be changed to make the library has a more small size.

## Compatibility

This version 1.0.0 is written with javascript es5 syntax for more compatibility without the need of a transpiler. We also make use of `querySelectorAll`. Anything newer than IE11 should be fine but if you run into issues please submit an issue so we can look into it.

Next major version will be both in es5 syntax and es6 modern synthax 

## Usage


Two functions are exported: `readonly` and `toggleReadonly`.

The first argument of any of them can be either:

- A selector.
- A single element.
- A collection of elements (_Array_ or _NodeList_).

### For `readonly`, two possible syntaxes:

- Single argument : 
```js
readonly('input, select, "#salary');
```

This will set the read-only state of matching elements.

- Two arguments

The second argument represents the read-only state argument. The expected values are :

- `true` : to make elements _read-only_
- `false` : to make elements _editable_ (not read-only)

**Example**: 

```js
readonly('#bool, #checkbox1, #checkbox2, #free, [name="radio-group"]', true);
```
The value of the read-only state of an element can also be changed using the property 'readOnly' that is added when an element has already been an argument or when it has already been a matching element of a selector argument.

For radio group, specify the nameof the group like this '[name="radio-group"]' instead of setting individually each radio of the group. Replace radio-group by the real name of the radio group.

After an element has been at least one time be an argument or a matching element of a selector argument, the value of read-only state can both be changed by calling the function `readonly` or by assigning a boolean value to the property 'readOnly'.

### For `toggleReadonly`, only one possible syntax:

```js
toggleReadonly('#salary, .nullable'));
```

This will toggle the read-only state of each matching element:

If an element was _read-only_, it became _editable_, or if an element was _editable_, it became _read-only_.


### jQuery

If you're using **jQuery** it'll be automatically installed as a plugin.

```js
$('input, select').readonly(true);
```


## Web Standards

Have you ever wondered why the `readonly` attribute doesn't work in `<select>` elements? Well, the whole thing is more complicated then one might think, but you can read all about it here: https://github.com/whatwg/html/issues/2311. You also could help advance the web standards by leaving a comment with why such feature would be useful to you.

## License

The MIT License © 2021 Marc KAMGA Olivier <kamga_marco@yahoo.com;mkamga.olivier@gmail.com>. See [LICENSE.md](LICENSE.md) for full notice.
