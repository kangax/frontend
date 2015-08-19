---
permalink: /css-coding-styleguide/naming/
layout: default
title: Naming
parent: CSS Coding Styleguide
---

- HTML elements should be in lowercase.

```scss
body, 
div {
```

- Classes should be lowercase.
- Avoid camelcase.
- Name things clearly.
- Write classes semantically. Name its function not its appearance.

```scss
// Bad
// Avoid uppercase
.ClassNAME { }

// Avoid camel case
.commentForm { }

// What is a c1-xr? Use a more explicit name.
.c1-xr { }
```

- Avoid presentation- or location-specific words in names, as this will cause problems when you (invariably) need to change the color/width/feature later.

```scss
// Bad
.blue
.text-gray
.100width-box

// Good
.warning
.primary
.lg-box
```

- Be wary of naming components based on content, as this limits the use of the class.

```scss
// Danger zone
.product_list

// Better
.item_list
```

- Don't abbreviate unless it’s a well-known abbreviation.

```scss
// Bad
.bm-rd

// Good
.block--lg
```

- Use quotes in type pseudo selectors.

```scss
// Good
.top_image[type=’text’] { }
```

- Name CSS components/modules with singular nouns.

```scss
.button { }
```

- Name modifiers and state-based rules with adjectives.

```scss
.is_hovered { }
```

- If your CSS has to interface with other CSS libraries, consider namespacing every class.

```css
.f18-component
```


## Naming Methodologies

When it comes to naming, the most important thing is consistency. The recommended way to do this is using an existing methodology like BEM (which stands for block, element, modifier), or use a custom one that’s clearly defined.

### BEM

BEM (which stands for block, element, modifier) structures CSS such that every entity is composed of (you guessed it) blocks, elements and modifiers. From [Harry Roberts](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

> The point of BEM is to tell other developers more about what a piece of markup is doing from its name alone. By reading some HTML with some classes in, you can see how – if at all – the chunks are related; something might just be a component, something might be a child, or element, of that component, and something might be a variation or modifier of that component. 

18F generally recommends using a modified BEM methodology outlined in the next subsection. However, you might want to use standard BEM when:
You need a naming scheme that general CSS developers will already be familiar with or an existing naming scheme hasn’t been consistent enough.
When you want to use Javascript to modify the BEM class names dynamically.

### Suggested custom methodology

The 18F recommendation for a naming methodology is a modified version of BEM. It still uses blocks, sections within blocks and modifiers, but doesn’t use as long a syntax.

```
.accordion
.accordion-item
.accordion-item-selected

.nav_bar
.nav_bar-link
.nav_bar-link-clicked
```



####Resources
- [article explaining BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
- [BEM website](https://en.bem.info/method/)


```scss
// block
.inset {
  margin-left: 15%;
  
  // element
  .inset__content {
    padding: 3em;
  }
}

// modifier
.inset--sm {
  margin-left: 10%;

  .inset__content {
    padding: 1em;
  }
}

// modifier
.inset--lg {
  margin-left: 20%;
}

```



## js- Flagged Classes
Don't attach styles to classes with a `js-` flag. These classes are reserved for javascript .

```css
// Bad
.js-people {
  color: #ff0;
}
```

### Rationale
A `js-` flagged class needs to be highly portable. Adding styles to it breaks that portability.

## test- Flagged Classes
Don't attach styles to classes with a `test-` flag. These classes are reserved for testing hooks such as those used by selenium .

```css
// Bad
.test-people {
  color: #ff0;
}
```