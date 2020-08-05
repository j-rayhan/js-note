# javascript

## Use Chrome DevTools
  1. Open the Command menu with the following shortcut:
      - windows：Ctrl + Shift + P 
      - macOS：Cmd + Shift + P
  
  2. Powerful screenshots 
      - Screenshot Capture full size screenshot(Take a screenshot of everything on a web page, including anything that doesn’t appear in the visual window) 
      - Screenshot Capture node screenshot (Capture exactly the content of a DOM element) 
      
  3. Reference the result of the last operation in the console
       - $_ ($_ is a special variable whose value is always equal to the result of the last operation in the console.)
       `'abcde'.split('').reverse().join('') -> 'abcde'.split('') -> $_.reverse() -> $_.join()`
       
  4. Resend the XHR request ( XHR to make a request to the back-end to get data)
      - Open Network panel
      - Click XHR button
      - Choose the XHR request that you want to resend
      - Right click -> RUN -> Replay XHR
      
  5. Monitor page load status 
      - we can capture screenshots of the page loading using Capture Screenshots under the Network panel.
      
  6. Copy Variables ( copy the value of a JavaScript variable somewhere else? )
      - The `copy` function is not defined by ECMAScript but is provided by Chrome
      
  7. Copy the image as the data URI
      - Open Network panel
      - Click IMG button
      - Choose the IMG 
      - Right click -> Select -> Copy image as data URL 
      
  8. Table object array 
      - table(users)
      
  9. Shortcut to hide an element 
      - select the element and press H on the keyboard
   
   
## Immediately-Invoked Function Expressions (IIFE)
  
  1. The natural function definition

```
function sayHi() {
    alert("Hello, World!");
 }

sayHi(); // shows "Hello, World!" as alert in browser.
``` 

  2. Function expressions
  ```
  let msg = "Hello, World!";
  let sayHi = function() {
      alert(msg);
  };

  sayHi(); // shows "Hello, World!" as alert in browser
  ```
   3. Named function expressions
   ```
   let fibo = function fibonacci() {
        // you can use "fibonacci()" here as this funciton expression has a name.
    };

    // fibonacci() here fails, but fibo() works
   ```
   4. Classical IIFE style 
   ```
   // Variation 1
    (function() {
        alert("I am an IIFE!");
    }());

    // Variation 2
    (function() {
        alert("I am an IIFE, too!");
    })();
   ```
   5. IIFEs and private variables
   ```
   (function IIFE_initGame() {
      // Private variables that no one has access to outside this IIFE
      let lives;
      let weapons;

      init();

      // Private function that no one has access to outside this IIFE
      function init() {
          lives = 5;
          weapons = 10;
      }
    }());
   ```
   6. IIFEs with a return value
   ```
   let result = (function() {
        return "From IIFE";
    }());

    alert(result); // alerts "From IIFE"
   ```
   7. IIFEs with parameters 
   ```
   (function IIFE(msg, times) {
        for (var i = 1; i <= times; i++) {
            console.log(msg);
        }
    }("Hello!", 5));
   ```
   8. Classical JavaScript module pattern
   ```
   let Sequence = (function sequenceIIFE() {
    
        // Private variable to store current counter value.
        let current = 0;

        // Object that's returned from the IIFE.
        return {
        };

    }());

    alert(typeof Sequence); // alerts "object"
   ```
   
   ```
   let Sequence = (function sequenceIIFE() {
    
        // Private variable to store current counter value.
        let current = 0;

        // Object that's returned from the IIFE.
        return {
            getCurrentValue: function() {
                return current;
            },

            getNextValue: function() {
                current = current + 1;
                return current;
            }
        };

    }());

    console.log(Sequence.getNextValue()); // 1
    console.log(Sequence.getNextValue()); // 2
    console.log(Sequence.getCurrentValue()); // 2
   ```
   9. The most important thing about an IIFE is that it can return a value/reference and you can assign that to a variable.
   
## JavaScript Closures 
    - A closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.
    1. Practical example with closures
    ```
    let sequence = () => {
        let count = 0;

        let counterBag = {};

        counterBag.increment = function () {
            count = count + 1;
        };

        counterBag.decrement = function () {
            count = count - 1;
        };

        counterBag.getValue = function () {
            return count;
        };

        // bag contains all the function references.
        // Think of an entire family's karmic bag.

        return counterBag;
    };

    let getSequence = sequence();
    // we don't need sequence any more.
    // We will see a better pattern instead of this in the next example.
    sequence = null;

    let a = getSequence.getValue(); // 0
    getSequence.increment();
    getSequence.increment();
    getSequence.increment();
    let b = getSequence.getValue(); // 3
    getSequence.decrement();
    let c = getSequence.getValue(); // 2

    console.log('A--->', a, '\nB--->', b, '\nC--->', c)
    ```
    
    2. Example with IIFE
    ```
    let sequenceObject = (() => {
        let count = 0;

        let counterBag = {};

        counterBag.increment = function () {
            count = count + 1;
        };

        counterBag.decrement = function () {
            count = count - 1;
        };

        counterBag.getValue = function () {
            return count;
        };

        // bag contains all the function references.
        // Think of an entire family's karmic bag.

        return counterBag;
    })();

    let a = sequenceObject.getValue(); // 0
    sequenceObject.increment();
    sequenceObject.increment();
    let b = sequenceObject.getValue(); // 2
    sequenceObject.decrement();
    let c = sequenceObject.getValue(); // 1

    console.log('A--->', a, '\nB--->', b, '\nC--->', c)
    ```
