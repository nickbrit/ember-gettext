# ember-gettext
[![Build Status](https://travis-ci.org/Wisembly/ember-gettext.svg?branch=master)](https://travis-ci.org/Wisembly/ember-gettext)

i18n gettext.js wrapper for Ember controllers and Handlebars templates


## Installation

1- Retrieve ember-gettext:

```
bower install ember-gettext --save
```

2- Include it in your project:

```html
<script src="./bower_components/gettext.js/dist/gettext.js"></script>
<script src="./bower_components/ember-gettext/lib/ember-gettext.js"></script>
```
or in your Brocfile if you use ember-cli.

3- Load your messages

Wherever it suits in your project, load your messages:

```javascript
Ember.I18n.loadJSON({...});
```

Your JSON format must be [the gettext.js required one](https://github.com/guillaumepotier/gettext.js#required-json-format)

4- Set the current locale

You could do it from your dom

```html
<html lang="fr">
```

or from javascript

```javascript
Ember.I18n.setLocale('fr');
```

## Usage

### In your controllers

  - Singular forms:

```javascript
Ember.I18n._t("I like apples.");
Ember.I18n._t("I like {{ fruit }}.", {fruit: "bananas"});
```

  - Plural forms:

You must use a `count` parameter to indicate gettext which plural form to choose

```javascript
Ember.I18n._n("There is {{ count }} apple", "There are {{ count }} apples", { count: 42 });
Ember.I18n._n("There is {{ count }} apple in the {{ where }}", "There are {{ count }} apples in the {{ where }}", { count: 12, where: "fridge" });
```

### In your templates

  - Singular forms:

```html
<p>{{_t "I like apples." }}</p>
<p>{{_t "I like {{ fruit }}." fruit="bananas" }}</p>
```

  - Plural forms:

You must use a `count` parameter to indicate gettext which plural form to choose

```html
<p>{{_n "There is {{ count }} apple" "There are {{ count }} apples" count=42 }}</p>
<p>{{_n "There is {{ count }} apple in the {{ where }}" "There are {{ count }} apples in the {{ where }}" count=12 where="fridge" }}</p>
```

  - Binded values

You could of course use binded values to be interpreted and automatically
re-rendered

```html
<p>{{_t "Hello {{ firstname }} firstnameBinding="user.firstname" }}</p>
<p>{{_n "There is {{ count }} apple in the {{ where }}" "There are {{ count }} apples in the {{ where }}" countBinding="fruits.count" whereBinding="fruits.container" }}</p>
```

## License

MIT
