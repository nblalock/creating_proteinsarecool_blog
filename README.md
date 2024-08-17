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
   - There are many text editors out there that would also work. I like Sublime the best, but I also have only used Sublime before...


### Step 2: Install Git on Windows machine
1. Type the following command to install Git:
   ```bash
   winget install --id Git.Git -e --source winget
   ```

### Step 3: Create repository on Github to maintain website
1. Navigate to your Github profile
2. Click on **repositories**
3. Click on **New** to create a repository.
4. Give the repository a name, description, and include a **README file**. The other settings depend on various things I am not an expert in so I would google about what license is best
   for what you want to do. I chose an MIT license (https://fossa.com/blog/open-source-licenses-101-mit-license/)

### Step 4a: Setup files for maintaining website on your local machine
1. Open **Command Prompt** from the taskbar
2. Navigate to your desktop to make it easy to see your files
   ```bash
   cd Desktop
   ```
3. Optional: You may need to set up a way to access your github account like using ssh. I explain how to do this below. If you already know about this and have this set up, skip to the next step.
4. Clone your github repository to this file (to find this navigate to your github repository and click on the button **Code**)
   ```bash
   git clone git@github.com:username/repository_name.git
   ```
   - You can check if your ReadMe file can not be seen in this file to make sure you cloned the repository.


### Setting up ssh to clone Github repository: Set up ssh to access Github repository
1. Start ssh agent
   ```bash
   start-ssh-agent.cmd
   ```
3. Generate new key
    ```bash
    ssh-keygen -t ed25519 -C "username@wisc.edu" -f C:"\Users\YourUsername\.ssh\id_ed25519"
    ```
    - You will then be asked to set up a passphrase
    - Verify passphrase by entering it again

3. Make sure ssh is running with your new key (assuming this is your first key, you may need to use ssh-add with a id_ed25519_new if you have made keys before in the past)
   ```bash
   start-ssh-agent.cmd
   ```
   You will be asked to enter your passphrase

4. Copy the new SSH public key to your clipboard: 
    ```bash
    type C:"\Users\YourUsername\.ssh\id_ed25519.pub" | clip
    ```

8. Go to GitHub and navigate to **Settings** > **SSH and GPG keys**.

9. Click on New SSH key to add the new key. 
    - Give it a title
    - Paste the key into the "Key" field. 
    - Save it.

10. Configure SSH to use the correct SSH key by editing the `.ssh/config` file to include:
     ```bash
    notepad C:"\Users\YourUsername\.ssh\config"
    ```
     - You may need to press okay about an error. Continue with notepad to make sure the configuration to use your ssh and key to clone your github repository
   
    # Use the new key for GitHub
    ```
    Host github.com
    HostName github.com
    User username@wisc.edu
    IdentityFile C:"\Users\YourUsername\.ssh\id_ed25519"
    ```

#### Pushing Edits to GitHub

1. **Navigate to the repository directory:**

    ```bash
    cd C:"\Users\YourUsername\repository_name"
    ```

2. **Check the status of your local repository:**

    ```bash
    git status
    ```

3. **Add your changes to the staging area:**

    ```bash
    git add .
    ```

    Use `.` to add all changed files, or specify the individual files.

4. **Commit your changes:**

    ```bash
    git commit -m "Your commit message"
    ```

5. **Push the changes to GitHub:**

    ```bash
    git push origin main
    ```
    - Replace `main` with the branch you're working on, if different.

---

#### Pulling Updates from GitHub

1. **Ensure you're in the repository directory:**

    ```bash
    cd RLXF_Projects
    ```

2. **Pull the latest changes:**

    ```bash
    git pull origin main
    ```

    Replace `main` with the branch you're working on, if different.

