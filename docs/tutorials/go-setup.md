# Setting up a dev container for Go
* Primary Author: [Vibhas Nair](https://github.com/nairvibhas18)

## Welcome!
Welcome to this tutorial! Here, you will learn how to create a simple project in the Go 
programming language. By the end of this tutorial, you will have created a basic Go
development container and a blank repository to track changes you make to your code.

## Prerequisites 
Before we start, make sure you have:
- **A GitHub account**: If you don’t have one yet, sign up at [GitHub](https://github.com/).
- **Git Installed**: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don't already have it
- **Visual Studio Code (VS Code)**: Download and install it from [here](https://code.visualstudio.com/).
- **Docker Installed**: This is required to run the dev container. Install it [here](https://www.docker.com/products/docker-desktop/).
- **Command-line basics**: Basic command line interface (CLI) commands will be necessary for this tutorial. This [link](https://aws.amazon.com/what-is/cli/#:~:text=A%20command%20line%20interface%20(CLI)%20is%20a%20text%2Dbased,operating%20system%20and%20the%20user.) provides a great tutorial if you need to brush up on your basics.

## Project Setup: Creating the Repository
### Step 1: Create a Local Directory and Initialize Git
A. Open your terminal or command prompt.

B. Create a new directory for your project:
```bash 
mkdir go-setup-tutorial
cd go-setup-tutorial
```
C. Initialize a new Git repository:
```bash
git init
```
D. Create a README.md file: 
```bash
echo "# Go Setup Tutorial" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Create a Remote Repository on GitHub
1. Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new) page.
2. Fill in the details as follows:
    - **Repository Name**: go-setup-tutorial
    - **Description**: "A basic tutorial for setting up a project in the Go programming language."
    - **Visibility**: Public 
> [!Warning]
> Do **not** initialize the repository with a README, .gitignore, or license.
3. Click **Create Repository**

### Step 3: Link your Local Repository to GitHub
1. Add the GitHub repository as a remote:
```bash 
git remote add origin https://github.com/<your-username>/go-setup-tutorial.git
```
Replace `your-username` with your GitHub username.

2. Check your default branch name with the subcommand `git branch`. If it isn't `main`. rename it to `main` using the `git branch -M main` command. Although `master` is used in older versions of `git`, `main` is the standard modern primary branch name.

3. Push your local commits to the GitHub repository:
```bash
git push --set-upstream origin main
```
> [!Note]
> The `-u` short flag also works in the place of `--set-upstream`
4. In your web browser, refresh your GitHub repository to verify that the commit you made locally has been successfully pushed to the remote repository. You can run `git log` locally to view the commit ID and message, which should match the most recent commit displayed on GitHub. This confirms that your changes have been pushed to the remote repository.