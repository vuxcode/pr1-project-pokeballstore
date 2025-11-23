# Local storage

## Phase 1
This is outside the course material. 
It will be more trial and error and Google MDN Web Docs and AI to help. 
Adding localStorage to my Glossary Trainer so words are saved between sessions.
Important stuff I learned:
- Can't name variables localStorage - it's already a built-in JavaScript object. I named mine storage instead but realized I might not even need it.
- Don't need a separate storage array - I figured out I can just use my existing glossary array:
  - Load from localStorage into glossary when the program starts
  - Save glossary to localStorage when I add words
  - listWords() already shows everything in glossary
- Option 4 should be different - Since listWords() already shows all words (including loaded ones), option 4 should do something else like:
  - Clear/delete the saved data  (can do this with prompts)
  - Import JSON by pasting text  (can do this with prompts)
  - Upload a file  (needs HTML input, not just prompts)

## Phase 2
Will this be possible to run on GitHub pages or does it need to be inside the same folder on the computer?
The localStorage.getItem is placed under the top variables so the program checks for saved data before continuing.
Now I will add .setItem at the end of the addWord function so words are saved both to the glossary (in memory live when the program is running) and to localStorage (persistent storage offline). 
What about exporting the list?

## Phase 3
Omg, it is working. 
Now I want to be able to delete the list.
https://stackoverflow.com/questions/7667958/clearing-localstorage-in-javascript
`localStorage.clear();`  will clear everything.
`localStorage.removeItem("name_of_localStorage_variable_to_remove");`
I will build a whole submenu.

## Phase 4

Copy local storage
I found .copy but it only seams to work in the console. 

https://stackoverflow.com/questions/55067628/json-example-confusing-me-about-json-parse-json-stringify-localstorage-setit
"Retrieving

    text = localStorage.getItem("testJSON");
        This line is retrieving the stored JSON string.
"
https://stackoverflow.com/questions/67406568/get-a-localstorage-item-value-and-set-it-as-a-variable

And to be able to load it, I need to make a variable. This part I cannot wrap my head around.
So I need to create a variable where I temporary store the .getItem 

# Phase 5

The export looks awful, will try to fix this later.

 Import words
https://www.freecodecamp.org/news/use-local-storage-in-modern-applications/

I need to make it a JSON.stringify and I have no idea how it will be sorted in English and Swedish.

But as a beginning I will do it similar to the start and just make a prompt and use localStorage.setItem.

Now the program breaks...

My research tells me: I need to run (copy) the addWord function again inside the import function and push the words to the glossary variable. But I need to add code that will treat space as the delimiter for splitting the words into 'var swe' and 'var eng'.

I actually looked at split back when we made the calculator to let the user write the problem in one prompt together with the operator signs (+, -, ×, ÷).

https://stackoverflow.com/questions/26425637/javascript-split-string-with-white-space

javascript
var string = "text to split"; 
string = string.split(" ");
var stringArray = new Array();
for(var i = 0; i < string.length; i++){
    stringArray.push(string[i]);
    if(i != string.length-1){
        stringArray.push(" ");
    }
}

I need to make it go one swe one eng one swe...

Now I am down a rabbit hole... A tab bit deeper than my knowledge atm..

Looping through an array taking 2 elements at a time!
In this case 2 words are two elements (adding synonyms to this? no way :'D)

https://stackoverflow.com/questions/12809776/can-a-for-loop-increment-decrement-by-more-than-one
https://stackoverflow.com/questions/10786569/looping-through-array-and-output-as-pairs-divider-for-each-second-element

Seems like I can use both for loop and a while loop. The for loop looks simpler to me.

for (var i = 0; i < arr.length; i += 2) {
    var title = arr[i];
    var len = arr[i+1];
}

# Phase 6

Add toLowerCase

# Phase 7

Remove the .JSON part from the export. 
Opposite of JSON.stringify is JSON.parse() as I use in the local storage function at the top of the program. 
Or if i can export the glossary without the json conversation 