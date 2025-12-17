# Local Storage

## Phase 1
This is outside the course material.
It will be more trial and error using Google, MDN Web Docs, and AI to help.
Adding localStorage to my Glossary Trainer so words are saved between sessions.

### Important stuff I learned:
- Can't name variables `localStorage` - it's already a built-in JavaScript object. I named mine `storage` instead but realized I might not even need it.
- Don't need a separate storage array - I figured out I can just use my existing `glossary` array:
  - Load from localStorage into glossary when the program starts
  - Save glossary to localStorage when I add words
  - `listWords()` already shows everything in glossary
- Option 4 should be different - Since `listWords()` already shows all words (including loaded ones), option 4 should do something else like:
  - Clear/delete the saved data (can do this with prompts)
  - Import JSON by pasting text (can do this with prompts)
  - Upload a file (needs HTML input, not just prompts)

---

## Phase 2
Will this be possible to run on GitHub Pages or does it need to be inside the same folder on the computer?

The `localStorage.getItem` is placed under the top variables so the program checks for saved data before continuing.

Now I will add `.setItem` at the end of the `addWord` function so words are saved both to the glossary (in memory live when the program is running) and to localStorage (persistent storage offline).

What about exporting the list?

---

## Phase 3
OMG, it is working!

Now I want to be able to delete the list.

https://stackoverflow.com/questions/7667958/clearing-localstorage-in-javascript

`localStorage.clear();` will clear everything.

`localStorage.removeItem("name_of_localStorage_variable_to_remove");`

I will build a whole submenu.

---

## Phase 4

### Copy local storage
I found `.copy` but it only seems to work in the console.

https://stackoverflow.com/questions/55067628/json-example-confusing-me-about-json-parse-json-stringify-localstorage-setit

**Retrieving:**
```javascript
text = localStorage.getItem("testJSON");
```
This line is retrieving the stored JSON string.

https://stackoverflow.com/questions/67406568/get-a-localstorage-item-value-and-set-it-as-a-variable

And to be able to load it, I need to make a variable. This part I cannot wrap my head around.
So I need to create a variable where I temporarily store the `.getItem`.

---

## Phase 5

The export looks awful, will try to fix this later.

### Import words
https://www.freecodecamp.org/news/use-local-storage-in-modern-applications/

I need to make it a `JSON.stringify` and I have no idea how it will be sorted in English and Swedish.

But as a beginning I will do it similar to the start and just make a prompt and use `localStorage.setItem`.

Now the program breaks...

My research tells me: I need to run (copy) the `addWord` function again inside the import function and push the words to the glossary variable. But I need to add code that will treat space as the delimiter for splitting the words into `var swe` and `var eng`.

I actually looked at `split` back when we made the calculator to let the user write the problem in one prompt together with the operator signs (+, -, ×, ÷).

https://stackoverflow.com/questions/26425637/javascript-split-string-with-white-space

```javascript
var string = "text to split"; 
string = string.split(" ");
var stringArray = new Array();
for(var i = 0; i < string.length; i++){
    stringArray.push(string[i]);
    if(i != string.length-1){
        stringArray.push(" ");
    }
}
```

I need to make it go one swe one eng one swe...

Now I am down a rabbit hole... A tad bit deeper than my knowledge at the moment.

### Looping through an array taking 2 elements at a time!
In this case 2 words are two elements (adding synonyms to this? No way :'D)

https://stackoverflow.com/questions/12809776/can-a-for-loop-increment-decrement-by-more-than-one

https://stackoverflow.com/questions/10786569/looping-through-array-and-output-as-pairs-divider-for-each-second-element

Seems like I can use both a for loop and a while loop. The for loop looks simpler to me.

```javascript
for (var i = 0; i < arr.length; i += 2) {
    var title = arr[i];
    var len = arr[i+1];
}
```

---

## Phase 6

Add `toLowerCase()`.

---

## Phase 7

Remove the JSON part from the export.

The opposite of `JSON.stringify` is `JSON.parse()` as I use in the local storage function at the top of the program.

Parse didn't solve it.

Or if I can export the glossary without the JSON conversion.

### Export function code:
```javascript
// ==== Export ==== 
function exportList() {
  if (glossary.length === 0) { // If empty 
    alert("No words to export") // Alert the user with this message
    return; // Then return 
}    

var exportText = ""; // Same as list text but different name for debugging and no message to the user

for (var i = 0; i < glossary.length; i++) {  // Part 1: var i = 0 (Initialization) Start counting at position 0, Part 2: i < glossary.length (Condition) Keep looping WHILE i is less than the total number of words

  exportText += glossary[i].swedish + "  " + glossary[i].english + "\n"; // We can skip the "index 0 -> 1 fix"
}
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for

https://stackoverflow.com/questions/12809776/can-a-for-loop-increment-decrement-by-more-than-one 
// Can I use this to fix the bug when adding three words?

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join

Opposite of the split:
```javascript
console.log(elements.join(""));
// Expected output: "FireAirWater"
```
Will try and add a space.

**BIG UPDATE: 20, Export is broken... back to the bench...**

My neighbour helped me and told me what my problem is:
```javascript
glossary.push({ swedish: swe.toLowerCase(), english: eng.toLowerCase() });
```
This is for adding to the list, not extracting from it. First I got the whole array but with the brackets and such.
I tried copying from the add word function.
Need to find a way to extract the information from within the array.

https://stackoverflow.com/questions/19590865/from-an-array-of-objects-extract-value-of-a-property-as-array

```javascript
function getFields(input, field) {
    var output = [];
    for (var i=0; i < input.length ; ++i)
        output.push(input[i][field]);
    return output;
}

var result = getFields(objArray, "foo"); // returns [ 1, 3, 5 ]
```

If I do the `output.push` twice and after I need to use `.join`.
Still broken... 
FIXED!

## Phase 8 

How should you return in the menu after adding words an so on. 
Fix the three word bug.

https://www.youtube.com/watch?v=JfHEtou8qb4

Lesson 05 - Operators

variable % 2 == 0 

A: This would check if the variable is an EVEN number. The result would be either true or false.
https://medium.com/@stitans28/javascript-remainder-operator-101-794f4df28c87
<img src="images/remainder_function.png" alt="Export bug screenshot" width="300">
How to add this to the import function? If it starts to count from 0, is 1 even?

function evenInput(num) {
   if  num % 2 === 0{
    console.log("valid input!");
   } else {
   alert("Please enter an even number of words.");
}
   }

let currentHour = 10;

let isMorning = currentHour < 12;
if (isMorning) {
  document.write('Good morning!');
}
//-----------------------------------------------------------------------------------------------------------------
function evenInput(num) {
  // COLIN: HERE YOU ARE TRYING TO DECIDE WHAT TO DO WITH THE NUMBER VARIABLE
  // IF THE NUMBER IS EVEN THEN... 
  if (num % 2 === 0) {
    // YOU ARE SAVING THE "TRUE" STATE INTO THE NUMBER VARIABLE
    number = true;
   }
   // WHAT SHOULD WE DO IF THE NUMBER IS ODD?
    else {
   alert("Please enter an even number of words.");
}
   }
 // ==== Import ====
function importList() {  // Copied the addWord and wordsList function and will add split to make so the user can paste a block of words 
  var data = prompt("Paste the words in order Swedish then English:\nOne space in between every word "); // paste text for example "trä wood vatten water"
  
  if (data) { // Check if user actually pasted something, otherwise the function will not run. Will it return to the menu, do I need to give invalid message or create a return?
    var words = data.split(" "); // Split the text by spaces into an array of individual words ["trä", "wood", "vatten", "water"] (What about case sensitivity?) data.split(" ") - data is the variable, split is the function/method, and " " (the space) is the separator/parameter.
    // COLIN: I THINK YOU WANT TO USE THE "evenInput" FUNCTION HERE FIRST!
    // THEN YOU WANT TO CHECK IF THE NUMBER IS TRUE OR FALSE
    // YOU COULD END THE FUNCTION HERE IF THE NUMBER IS NOT EVEN

    // I WOULD
 
    // Loop through the array, taking 2 words at a time

https://stackoverflow.com/questions/3212477/can-you-write-nested-functions-in-javascript

## Phase 9

End phase. Will just go to github and copy the old import function that works. And will leave it erup to the user to add correct amount of words. Sorry user, I tried my best.

It works. I am kind of happy... 