# Creating static website from scratch for blog about protein engineering

I decided to create a blog to document thoughts from literature related to Machine Learning for Protein Engineering, collaborate with other protein engineers, and learn new programming languages. As an additional challenge, I decided to use a Windows machine rather than my typical Mac.

## Objectives
1. Save and organize my thoughts from literature.
2. Collaborate with other protein engineers.
3. Learn and apply new programming languages like Markdown, html, CSS, and Javascript.
4. Learn to use a Windows environment.

## Step-by-Step Guide

### Step 1: Install VSCode
1. Open the **Start Menu** and search for "Command Prompt."
2. Right-click on **Command Prompt** and select "Pin to taskbar" for easy future access at the bottom of your desktop screen.
3. Open **Command Prompt** from the taskbar.
4. Type the following command to install Visual Studio Code:
   ```bash
   winget install Microsoft.VisualStudioCode
   ```
6. Press enter to install
*There are many text editors out there that would also work. I like Sublime the best, but I also have only used Sublime before...

### Step 2: Install Git on Windows machine
1. Type the following command to install Git:
   ```bash
   winget install --id Git.Git -e --source winget
   ```

### Step 3: Create repository on Github to maintain website
1. Navigate to your Github profile
2. Click on **repositories**
3. Click on **New** to create a repository.
4. Give the repository a name, description, and include a **README file**. The other settings depend on various things I am not an expert in so I would google about what license is best for what you want to do. I chose an MIT license (https://fossa.com/blog/open-source-licenses-101-mit-license/)

### Step 4a: Setup files for maintaining website on your local machine
1. Open **Command Prompt** from the taskbar
2. Navigate to your desktop to make it easy to see your files
   ```bash
   cd Desktop
   ```
3. Create a file called public using command line (directions for creating a minimal website are adapted from https://tinyprojects.dev/guides/tiny_website)
   ```bash
   mkdir public
   ```
4. Navigate to the public file
    ```bash
   cd public
   ```
5. Optional: you may need to set up a way to access your github account. Step 4a below explains how to do this. Otherwise, skip this step.
6. Clone your github repository to this file (to find this navigate to your github repository and click on the button **Code**)
   ```bash
   git clone git@github.com:nblalock/creating_proteinsarecool_blog.git

### Step 4b: Set up ssh to access Github repository
1. Start ssh agent
   ```bash
   start-ssh-agent.cmd
   ```
3. Generate new key
    ```bash
    ssh-keygen -t ed25519 -C "username@wisc.edu" -f C:"\Users\YourUsername\.ssh\id_ed25519"
    ```
    You will then be asked to set up a passphrase
    Verify passphrase by entering it again

4. Add your new SSH key to the SSH agent: 
    ```bash
    ssh-add C:"\Users\YourUsername\.ssh\id_ed25519"
    ```

5. Copy the new SSH public key to your clipboard: 
    ```bash
    type C:\Users\YourUsername\.ssh\id_ed25519_new.pub | clip
    ```

6. Go to GitHub and navigate to Settings > SSH and GPG keys.

7. Click on New SSH key to add the new key. 
    - Give it a title and paste the key into the "Key" field. 
    - Then save it.

8. Configure SSH to use the correct SSH key by editing the `.ssh/config` file to include:
     ```bash
    notepad C:"\Users\YourUsername\.ssh\config"
    ```
   
    # Use the new key for GitHub
    Host github.com
    HostName github.com
    User username@wisc.edu
    IdentityFile C:\Users\YourUsername\.ssh\id_ed25519
    ```


