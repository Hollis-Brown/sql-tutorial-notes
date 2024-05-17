# Pre & Post Scripts

- Open terminal, type and run: npm init -y
- This command creates a package.json file
- Next, in the terminal type and run: npm run test
- This will create a package.json file
## Here's what's in the package.json file
```json
{
  "name": "pre-post",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```
<hr>

## I will add a script to the code
- The ampersand in between the code on line 15 (above) shows me that I can write multiple commands per line. 
- Now I will add the code on line 35 (being sure to use a slash to escape the quotation marks)
```json
{
  "name": "pre-post",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "hollis": "echo \"Hello Hollis\" ",
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```
- Next, in the terminal type and run: npm run hollis
- Look for a response that says "Hello Hollis" - cool!

 <hr>

## I will add pre and post to the code
- As soon as I create a name (as above) `hollis: ...` I automatically get the ability to create pre and post.
```json
{
  "name": "pre-post",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "hollis": "echo \"Hello Hollis\" ",\
    "prehollis": "",
    "posthollis": ""
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

- This is useful for instance when I want to have a script that is going to check to see if I have a .gitignore file and maybe clear out its contents and write something to that file. 
```json
{
  "name": "pre-post",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "ignore": "echo \"\"  > .gitignore",
    "preignore": "touch .gitignore",
    "postignore": "echo \".gitignore\n.vscode\nnode_modules/\" > .gitignore "
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```
- A single > clears out the file
- Two >>'s append it to the file
- This effectively adds a blank line to the file each time the command is executed.
- In the terminal, type and run: npm run ignore

## Here's the output of inside of the newly created `.gitignore` file
![Gitignore file](https://i.imgur.com/iEcr1ep.png)

- If I run the file again, it simply duplicates the .gitignore file's contents - thus the result of running the append use two >>'s command. 
- Now change the code to use a single >.

## Here's how Pre & Post Scripts work in your Node.js project:

1. **Script Definition**: When you define a script in the scripts section of your package.json file (e.g., "test" or "hollis"), Node.js automatically allows you to create pre- and post-scripts for it.

2. **Pre-script Execution**: A pre-script is a script that runs before the main script you defined. This allows you to prepare the environment or perform checks before the actual task is executed.

3. **Script Naming**: The name of the pre-script follows the format pre<script_name>. For example, if your script is named "test", the corresponding pre-script would be named "pretest".

4. **Post-script Execution**: A post-script is a script that runs after the main script has finished execution. This allows you to perform cleanup tasks, log results, or trigger further actions based on the main script's outcome.

5. **Script Naming**: The name of the post-script follows the format post<script_name>. For example, if your script is named "test", the corresponding post-script would be named "posttest".

#### In summary, Pre & Post Scripts in your Node.js package.json automate tasks around scripts, streamlining development. They handle setup, validation (before execution), and logging, cleanup (after execution), keeping scripts focused and projects organized.