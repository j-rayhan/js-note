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
   
  
   
