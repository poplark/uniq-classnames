# unique-classnames

English | [简体中文](./README-zh_CN.md)


A simple javascript utility for conditionally joining classNames together, and none of the classNames are duplicated.

## Install

```sh
npm install unique-classnames --save
```

or

```sh
yarn add unique-classnames
```

## Usage

The arguments can be string, number, array and object.

string:

```js
import classnames from 'unique-classnames';
classnames('foo bar', 'foo2 bar2'); // => 'foo bar foo2 bar2'
classnames('foo bar', 'foo bar2'); // => 'foo bar bar2'
```

number:

```js
import classnames from 'unique-classnames';
classnames(1, 2, 3); // => '1 2 3'
classnames(1, 2, 2, 2, 3, 3); // => '1 2 3'
```

array:

```js
import classnames from 'unique-classnames';
classnames([1, 2, 'foo', 'bar']); // => '1 2 foo bar'
classnames([1, 2, 'foo', 'bar'], ['foo', 1, 2]); // => '1 2 foo bar'
```

object:

```js
import classnames from 'unique-classnames';
classnames({foo: true, 'bar': true}); // => 'foo bar'
classnames({foo: true, 'bar': false}); // => 'foo'

classnames({foo: 1, 'bar': 1}); // => 'foo bar'
classnames({foo: 0, 'bar': 1}); // => 'bar'

classnames({'foo bar': true}); // => 'foo bar'
classnames({'foo bar': true}, {bar: false}); // => 'foo'
classnames({'foo bar': true}, {foo: false}, 'foo'); // => 'foo bar'
```

All types can be combined with each others. And if there are more than one 'className' with the same name, and the last one will cover the front one. For example:

```js
classnames({'foo bar': true}, {foo: false}, 'foo'); // => 'foo bar'
```

The 'foo' of {foo: false} will cover the one in 'foo bar' of {'foo bar': true}, but it will be covered by the last argument 'foo', so the result is {foo: true, bar: true} => 'foo bar'
