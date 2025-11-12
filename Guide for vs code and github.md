 🧭 VS Code + GitHub Classroom Setup Guide 


Hello and welcome!


⚠️ Step 0 — Before You Start 👉 Make sure you have accepted the Classroom link from Collin before doing anything else. This creates your own private assignment repository inside the school’s GitHub organization. 

If you skip this step, nothing will connect correctly later!


 “How to connect VS Code to GitHub on Windows” 🎯 


Goal Show how to: Install Git on Windows/mac/linux

 Sign in to GitHub from VS Code Clone or upload a project No terminal commands required at all.

 Start with Visual Studio Desktop

 https://code.visualstudio.com/download

 🪄 Step 1 — Install Git

Narration:

“Before VS Code can talk to GitHub, we need Git — the program that does the saving and syncing.”

Visuals:

Go to git-scm.com → click Download for Windows.

Run the installer → keep every default option.

When finished, click Finish and close the installer.

Restart VS Code so it recognizes Git.


https://github.com/git-guides/install-git


Install Git on Windows through Visual Studio Code

GitHub integration is provided through the GitHub Pull Requests and Issues extension.
To get started with the GitHub in VS Code, you'll need to create an account and install the GitHub Pull Requests and Issues extension.
Once you've installed the GitHub Pull Requests and Issues extension, you'll need to sign in. Follow the prompts to authenticate with GitHub and return to VS Code.

Note: You can perform actions like, you can search for and clone a repository from GitHub using the Git: Clone command in the Command Palette (Ctrl+Shift+P) or by using the Clone Repository button in the Source Control view (available when you have no folder open).
Learn more here https://code.visualstudio.com/docs/sourcecontrol/github


And one more link https://code.visualstudio.com/docs/getstarted/extensions




🔐 Step 2 — Sign in to GitHub from VS Code

Narration:

“Now we’ll connect VS Code to your GitHub account so you can push and pull your code.”

Visuals:

In VS Code, click the Account icon (bottom-left corner).

Choose ‘Sign in to GitHub’.

A browser window opens → click Authorize Visual Studio Code.

Return to VS Code — your GitHub username now appears in the corner. ✅

If it is the first time you log on, you need to do 2fa.





🗂️ Step 3 — Open or clone your project

Narration:

“Let’s bring a project into VS Code.”

Visuals:

To clone from GitHub:

Press Ctrl + Shift + P.

Type ‘Git: Clone’.

Paste your GitHub repo link.

Choose a folder → click ‘Open’.

To start a new project:

Click File → New Folder.

Open that folder in VS Code.

Add some files to it.


Now, your repo should be downloaded to that folder you created. 







💾 Step 4 — Publish to GitHub

Narration:

“Now we’ll send the project up to GitHub.”

Visuals:

Open the Source Control panel (branch icon on left).

Click ‘Publish to GitHub’.

Pick a name → choose Public or Private → click ‘Publish Repository’.

VS Code creates the repo on GitHub and pushes your files automatically. 🎉

(You’ll see the confirmation link appear in the Output panel — click to open it in GitHub.)


I just made a change in my index and created/changed the guide. Lets save ctrl + s 





🧠 Step 5 — Edit, Save & Sync

Narration:

“Every time you change something, commit and sync it to keep GitHub up to date.”

Visuals:

Make a small edit to any file.

Source Control → click + to stage changes.

Write a commit message → click Commit.

Then click Sync Changes (🔁) to upload to GitHub.