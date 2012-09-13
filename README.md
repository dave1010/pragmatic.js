# Pragmatic.js code style guidelines

* `function name() { }` or `var name = function() { };` for named functions
* `function() { }` for anonymous functions
* Use short and concise expressions
* Prefer functional programming over for or while loops
* Use curly braces for all control flow statements such as `if` & friends
* Always write semicolons that are optional
* Use long, descriptive variable and method names
* Use blank lines to separate "paragraphs" of code for readability
* Use comments to describe non-obvious code behavior

### Examples

Here are some examples modified from [Zepto.js][zepto].

```javascript
// typical helper function
function eachEvent(events, fn, iterator) {
  if ($.isObject(events)) {
    $.each(events, iterator);
  } else {
    events.split(/\s/).forEach(function(type){ iterator(type, fn) });
  }
}

// shortcut methods for `.bind(event, fn)` for each event type
('focusin focusout load resize scroll unload click dblclick '+
'mousedown mouseup mousemove mouseover mouseout '+
'change select keydown keypress keyup error').split(' ').forEach(function(event) {
  $.fn[event] = function(callback){ 
    return this.bind(event, callback);
  }
});

// from Zepto core, $.fn.siblings implementation
function filtered(nodes, selector) {
  return selector === undefined ? $(nodes) : $(nodes).filter(selector)};
}

$.fn.siblings = function(selector){
  return filtered(this.map(function(i, el){
    return slice.call(el.parentNode.children).filter(function(child){ 
      return child!==el;
    });
  }), selector);
};
```

### About

This is a fork Thomas Fuchs' [Pragmatic.js][fork]. While most of his rules make sense, 
the ones about ommitting semicons and brances are a [bad idea][bad] in many people's opinoipns
(including my own and the guy whocreated JavaScript).

### Contribute

I welcome contributions—this guide is very basic at the moment and should probably have some more
guidelines for specific situations and how to get started. You know where the fork & pull request
buttons are.

### License

Pragmatic.js is licensed under the terms of the MIT License.

  [fork]: https://github.com/madrobby/pragmatic.js
  [zepto]: http://zeptojs.com/
  [bad]: http://brendaneich.com/2012/04/the-infernal-semicolon/