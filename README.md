# Javascript - Lite Brite
Build an interactive Lite Brite utilizing JavaScript and jQuery. The project will be a grid of elements that change color when clicked, then have the ability to blink.  When complete, the user will be able to draw a picture with multiple colors using the program.

## Directions - HTML

1. Some of the html has been done for you. Open the **index.html** file and, inside the body, add a div with a class of `color-picker`.

2. In the `color-picker` div, add four more divs.

3. The first div should use the following classes: `select-color`, `cyan`, and `not-selected`. The text **CYAN** should appear on the page.

4. The second div should use the following classes: `select-color`, `yellow`, and `not-selected`. The text **YELLOW** should appear on the page.

5. The third div should use the following classes: `select-color`, `magenta`, and `not-selected`. The text **MAGENTA** should appear on the page.

6. The fourth div should use the class `toggle-blink` and the text **Blink!** should appear on the page.

7. Now the fun part, the "board" has 36 rows. Each row contains either 28 or 27 circles. You'll set up two of these rows, then copy and paste the rest.

8. Create a new div with class `row`.

9. Inside this row, create 28 divs each with class `box`. *(Hint: Create one and copy and paste)*

10. Now, copy and paste that row below itself. Delete one of the `box` divs.

11. Finally, copy both rows and paste them in 17 more times.

## Directions - CSS

1. Most of the CSS has been done for you. You just have to fine tune a few things.

2. 

## Directions - JavaScript

1. To get started, open *script.js*, write a function named `main`, with no parameters. You can write all of your code inside the main function for this project. Then declare the document ready jQuery function, and make `main` its callback function.

2. In the top left corner, there are three `<div>`s that will let the user choose which color they'd like to use. A user should be able to click on them. Start by writing a click handler on the class `.select-color`.

3. Once a user clicks on one of the `.select-color` elements, we need to save that selection in our JavaScript file. We can do that by creating a variable named `selectedColor` inside the `click` function. In order to get the element's class that we clicked on, we can write this:
    ```javascript
    var selectedColor = $(this).attr('class');
    ```

    This is a new jQuery method: `.attr()`. It stands for attribute and it returns the "class" attributes on the HTML element we clicked. For instance, if we had `<div class='main-header'>`, `$('div').attr('class')` would return 'main-header'.

4. Now that we have these classes, we can use an if/else or switch statement to set a color on the boxes in the grid.

5. We need to take the selected color, then use that selected color when clicking on the `.box` elements that make up the grid. We can do this by making a making a variable that will hold the color class. Make a variable named `colorClass` outside the `click` function, and set it to an empty string: `''`.

6. Inside the `click` function, set `colorClass` equal to the color. For instance, if *select-color cyan not-selected* is selected, set the `colorClass` variable to *cyan*. (Notice, there are classes in the CSS named `.cyan`, `.magenta`, and `.yellow`).

7. To finish out the .select-color click function, let's make the buttons light up when they are selected. Currently, the .select-color class has an not-selected class, which makes the color of the word and underline grey. At the bottom of the click function, remove the class the not-selected class on `$(this)`, with the jQuery function `removeClass`. `removeClass` is new, but works exactly like `toggleClass()`.

8. There's one small issue: when you click on multiple colors, they all stay lit up. To add the class `not-selected` to the other colors, add this line to the last line of the click function:
    ```javascript
    $(this).siblings().addClass('not-selected');
    ```
    We have not learned `siblings` and `addClass` methods yet. In short, this code will make sure that all the other elements next to the clicked element receive the `not-selected` class.

9. Now we can choose a color, but we need to apply the color class to the boxes in the grid. Every box in the grid has a class of `box`. When we click on one of those boxes, let's toggle whichever class is inside the `colorClass` variable. Start by writing another click function outside the one we previously wrote. The selector should select all elements with '.box'.

10. Inside the .box click function, use $(this) to select the box that was clicked, and toggle the class colorClass.

Test it out: you should be able to click a color, then click a box in the grid, and it should change to the selected color!

11.
The last task is to make our grid blink when we click the "Blink" button.

Write another click function, but this time select '.toggle-blink'.

12.
Inside the click function, we need to do three things:

Make sure colorClass is not empty.
Make the blink button light up.
Make the boxes in the grid toggle between an opacity of 1, and of 0.7, over and over.
We can make sure colorClass is not empty by writing an if/else statement that looks like:

if (colorClass) {
  // the rest of the code in here
}
colorClass starts out equal to an empty string: '', which evaluates to false. When we click a color, it will be set to a color, like cyan, which will evaluate to true.

13. Inside the if/else statement, let's make the button light up. Toggle the class opacity on the '.toggle-blink' element.

14. Finally, we want to toggle the opacity of the elements we clicked, automatically. There is a JavaScript function that can help us with this called setInterval(). setInterval() takes a function, and a number of milliseconds, and will call the function every millisecond interval that we set. It looks like this:
    ```javascript
    setInterval(function() {
      // do something here repeatedly
    }, 500);
    ```  
    This example will execute the function every 500 milliseconds. Inside the .toggle-blink click function, write a setInterval, with a function that toggles the class blink on the classes .box.magenta, .box.yellow, .box.cyan. Then, set the interval to 350 milliseconds.

15. Click on the colors in the top left and draw a picture in the grid. Then, click on the "Blink" button, and watch your drawing shimmer! Note: Clicking the "Blink" button again will not stop the Lite Brite from blinking. In order to stop the interval from toggling the opacity class, you'd need to use clearInterval. If you're curious on how to use this function, check out this documentation. Alternatively, you can reload the preview page to reset your Lite Brite.
