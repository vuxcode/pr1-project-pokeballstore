# Local storage

## Phase 1
This is outside the course material. 
It will be more trial and error and Google MDN Web Docs and AI to help. 

Adding localStorage to my Glossary Trainer so words are saved between sessions.
Important stuff I learned:

Can't name variables localStorage - it's already a built-in JavaScript object. I named mine storage instead but realized I might not even need it.
Don't need a separate storage array - I figured out I can just use my existing glossary array:

Load from localStorage into glossary when the program starts
Save glossary to localStorage when I add words
listWords() already shows everything in glossary


Option 4 should be different - Since listWords() already shows all words (including loaded ones), option 4 should do something else like:

Clear/delete the saved data  (can do this with prompts)
Import JSON by pasting text  (can do this with prompts)
Upload a file ❌ (needs HTML input, not just prompts)


## Phase 2

Will this be possible to run on github pages or does it need to be inside a same folder on the computer?

The localStorage.getItem is placed under the top variables so the program checks for saved data before continuing.
 Now I will add .setItem at the end of the addWord function so words are saved both to the glossary (in memory live when program is running) and to localStorage (persistent storage offline). 