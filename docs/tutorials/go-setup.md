# Setting up a dev container for Go
* Primary Author: [Vibhas Nair](https://github.com/nairvibhas18)

## Welcome!
Welcome to this tutorial! Here, you will learn how to create a simple project in the Go 
programming language. By the end of this tutorial, you will have created a basic Go
development container and a blank repository to track changes you make to your code.

## Part 0: Prerequisites 
Before we start, make sure you have:
- **A GitHub account**: If you don’t have one yet, sign up at [GitHub](https://github.com/).
- **Git Installed**: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don't already have it
- **Visual Studio Code (VS Code)**: Download and install it from [here](https://code.visualstudio.com/).
- **Docker Installed**: This is required to run the dev container. Install it [here](https://www.docker.com/products/docker-desktop/).
- **Command-line basics**: Basic command line interface (CLI) commands will be necessary for this tutorial. This [link](https://aws.amazon.com/what-is/cli/#:~:text=A%20command%20line%20interface%20(CLI)%20is%20a%20text%2Dbased,operating%20system%20and%20the%20user.) provides a great tutorial if you need to brush up on your basics.

## Part 1: Project Setup: Creating the Repository
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

## Part 2: Setting Up the Development Environment 
### What is a Development (Dev) Container?
A development (dev) container is a preconfigured environment designed to ensure consistency across different machines. Essentially, it's a "mini computer" within your computer, equipped with everything you need for a specific project—such as the appropriate programming language, tools, libraries, and dependencies. Dev containers are typically set up using Docker to create isolated and reliable development environments.
In the tech industry, complex projects often rely on specific tools and dependencies to function correctly. Without a dev container, each developer must manually configure their environment, which can lead to errors, inconsistencies, and wasted time. Dev containers solve this problem by providing an identical setup for everyone on the team, eliminating the infamous "it works on my machine" issues. They also make onboarding easier, enabling new team members to start contributing quickly with minimal setup.

Let's create our development container:

### Step 1: Add Development Container Configuration 
1. In VS Code, open the `go-setup-tutorial` directory 
> [!Note]
> You can do this by clicking File > Open Folder 
2. Install the **Dev Containers** extension for VS Code by searching for the one made by **Microsoft** in the extensions tab of VS Code
3. Create a hidden `.devcontainer` configuration directory in the root of your project with this file inside of it:
`.devcontainer/devcontainer.json`
4. Specify environment variables:
Inside the `devcontainer.json` file we need to specify the configuration of our development environment:
    - **name**: Specify a descriptive name for your dev container  (i.e. "Go Dev Container")
    - **image**: We will use the latest version of a Go environment, but if you would like to create your own or check out other base images for other language environments, you can click this [link](https://hub.docker.com/r/microsoft/vscode-devcontainers).  
    - **customizations**: Here we can add useful configurations to VS Code like the Go extension made by **Google** found in the Extensions marketplace. By adding extensions here, we can make sure that other who work on this project have these extensions installed in their dev containers automatically. 
    - **postCreateCommand**: Once the dev container is created, we will run the command defined by postCreateCommand. For us, since this is a simple project, we don't have any necessary dependencies so we will just run `go version` to output the version of Go we have. 

> [!Note]
> This simple project currently doesn't have any dependencies that we would need to install, but if we did, we would need to create a Go dependency configuration file, like `requirements.txt.` which would be created in the root directory, that would list all of the dependencies we would need for the project. We would then need to install these dependencies after the dev container is created by running a command in the `postCreateCommand` variable. 

```bash
{
  "name": "Go Dev Container",
  "image": "mcr.microsoft.com/vscode/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.go"]
    }
  },
  "postCreateCommand": "go version"
}
```

### Step 2: Reopen the Project in a VS Code Dev Container
Reopen the project in the container by pressing **Ctrl+Shift+P** (or **Cmd+Shift+P** on Mac), searching for **"Dev Containers: Reopen in Container,"** and selecting the option. The setup process may take a few minutes as the Docker image is downloaded. After the dev container setup is complete, close the current terminal tab by clicking the trash can icon, then open a new terminal pane within VS Code to begin working.

## Part 3: Running Your First Program in Go
