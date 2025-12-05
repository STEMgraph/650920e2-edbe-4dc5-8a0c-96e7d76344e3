<!---
{
  "id": "650920e2-edbe-4dc5-8a0c-96e7d76344e3",
  "teaches": "Git: Using Git over SSH on Your Own Remote-Machine",
  "depends_on": ["474307f2-a30c-4639-9379-298bf1a4c00b", "8c79cd1f-f6bd-4930-b62c-b2970c412735"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-01",
  "keywords": ["git", "ssh", "remote", "repository"]
}
--->

# Git: Using Git over SSH on Your Own Remote-Machine

## 1) Introduction

You've already learned how to initialize a repository, stage and commit changes, and push them to a remote. You've also practiced the difference between local and remote repositories.

In this exercise, you'll take the next step by working with **your own remote machine** using **SSH**. You'll create a Git repository on the remote server and configure your local repository to push to and pull from it. This workflow mimics how software developers collaborate using a central repository server like GitHub — but you're hosting it yourself!

This is a great way to:

- Understand what happens behind hosted Git services
- Practice with real-world SSH-based Git workflows
- Gain confidence in navigating both local and remote machines

## 2) Tasks

1. **Connect to Your Remote Machine**

   ```bash
   ssh <your-user>@<your-remote-host>
   ```

   - Navigate to or create a directory for your remote Git repositories (e.g., `mkdir -p ~/repos/myproject && cd ~/repos/myproject`)
   - Initialize a **bare repository**:

     ```bash
     git init --bare
     ```

   - Exit the remote session:

     ```bash
     exit
     ```

2. **Set Up a Local Repository**

   - On your **local machine**, create a project directory:

     ```bash
     mkdir myproject && cd myproject
     git init
     touch README.md
     git add README.md
     git commit -m "Initial commit"
     ```

   - Add the remote repository using SSH:

     ```bash
     git remote add origin <your-user>@<your-remote-host>:~/repos/myproject
     ```

3. **Push Your Work to the Remote**

   ```bash
   git push -u origin master
   ```

4. **Clone the Project Elsewhere (Optional)**

   - On a different machine (or a different directory), clone the repo:

     ```bash
     git clone <your-user>@<your-remote-host>:~/repos/myproject
     ```

5. **Make a Change and Push Again**

   - Locally, edit the README or add a new file:

     ```bash
     echo "Hello from SSH" >> README.md
     git add README.md
     git commit -m "Update via SSH"
     git push
     ```

6. **Pull from Another Machine or Clone Directory**

   - If you cloned elsewhere: run `git pull` to get the latest changes.

## 3) Questions

- What is the difference between a regular and a bare repository?
- Why is a bare repository required on the remote?
- What is the structure of a Git SSH remote URL?
- What happens if the SSH key or password is not accepted?
- What output do you get from `git remote -v`?
- Can you clone your remote repo from another machine?

## 4) Advice

Using Git over SSH to your own machine is a powerful skill — you're not relying on any third-party hosting. Make sure your SSH access is secured with strong keys or passwords. Always double-check file permissions on your remote repo and avoid giving write access to everyone.

This setup is the basis for advanced Git workflows with custom CI/CD pipelines or self-hosted Git servers like Gitea, Gitolite, or GitLab.

Once you're confident, try pushing and pulling between multiple machines to simulate real team workflows!

