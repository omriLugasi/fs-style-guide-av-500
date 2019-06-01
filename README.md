# Anyvision JavaScript Style Guide
*A mostly reasonable approach to JavaScript*

[![Build Status](https://travis-ci.org/omriLugasi/fs-style-guide-av-500.svg?branch=master)](https://travis-ci.org/omriLugasi/fs-style-guide-av-500)


## Table of Contents
 1. [If Else and the things between](#if-else-and-the-things-between)
 2.




## If Else and the things between

### One liner if "ternary operator"

```javascript
  // bad
  const value = condition ? 60 : anotherCondition ? 50 : 40

  // good
  let value = 60
  if (!condition) {
    value = anotherCondition ? 50 : 40
  }

```

  ```javascript

  // bad
  const value = condition ? true : false

  // good
  const value = !!condition

  // bad
  const value = condition ? false : true

  //good
  const value = !condition

  ```

```javascript

  // bad
   const aVeryVeryVeryLongCondition = veryVeryLongConditionName ? { name: 'anyvision', companyId: '20019292982272661' } : { name: 'seachFace', companyId: '289282871817281272' }

   // bad
   const aVeryVeryVeryLongCondition = veryVeryLongConditionName ?
   { name: 'anyvision', companyId: '20019292982272661' } :
   { name: 'seachFace', companyId: '289282871817281272' }

   // bad
   const aVeryVeryVeryLongCondition = veryVeryLongConditionName ?
   { name: 'anyvision', companyId: '20019292982272661' }
   : { name: 'seachFace', companyId: '289282871817281272' }


  // good
   const aVeryVeryVeryLongCondition = veryVeryLongConditionName
   ? { name: 'anyvision', companyId: '20019292982272661' }
   : { name: 'seachFace', companyId: '289282871817281272' }

  ```

```javascript

  // bad
   let num = 0
   // more code ...
   // more code ...
   condition ? num = 6 : num = 90

  // good
   let num = 0
    // more code ...
    // more code ...
   num = condition ? 6 : 90

  ```

  ```javascript

  // bad
  function getElements() {
    condition ? getItems() : getUsers()
  }

  //good
  function getElements() {
    const invokeFunc = condition ? getItems : getUsers
    invokeFunc()
  }

  //better
  function getElements() {
    if(condition) {
      return getItems()
    }
    getUsers()
  }

  ```

### Return number with if inside function scope

```javascript

 //bad
function getAverageAge(condition, anotherCondition) {
 let number = 0
 if(condition) {
   number = 20
 } else if(anotherCondition) {
   number = 40
 } else {
   number = 38
 }
 return number
}

 //good
 function getAverageAge(condition, anotherCondition) {
   if(condition) {
     return 20
   }
   return anotherCondition ? 40 : 38
 }
```

### JSX render function with if

  ```javascript

  // bad
  function renderItems(items) {
   if(item && items.length) {
    return (
       <JSX />
     )
   }
  }

  //good
 function renderItems(items) {
   if(!items || !item.length) {
     return null
   }
   return <JSX />
  }

  ```
