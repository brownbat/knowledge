# How to Setup Oh-My-Zsh with Autocomplete

Zsh and Oh My Zsh improves the terminal experience on Linux with autocomplete and suggestions.

## Step 1: Install Zsh

Ensure Zsh is installed on your system. You can install it via your Linux distribution's package manager. For example, on Debian/Ubuntu-based systems, use:

```bash
sudo apt update && sudo apt install zsh
```

## Step 2: Make Zsh your default shell

Change your default shell to Zsh with:

```bash
chsh -s $(which zsh)
```

Log out and back in to see the change.

## Step 3: Install Oh My Zsh

Oh My Zsh is a community-driven framework that offers plugins to manage the zsh configuration.

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Step 4: Enable Plugins

OMZ comes with a variety of plugins to extend its functionality built in, and others can be downloaded to enhance it.

autosuggestions, autocomplete, and fast-syntax-highlighting are powerful additions.

Clone the repos
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/marlonrichert/zsh-autocomplete.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autocomplete
git clone https://github.com/zdharma/fast-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```

## Step 5: Apply the Changes

Edit ~/.zshrc to add:
plugins=(git z python zsh-autosuggestions zsh-autocomplete fast-syntax-highlighting)
and
ZSH_THEME="agnoster"

```bash
source ~/.zshrc
```

## Additional Plugins

If you have other specific functionalities in mind, you can explore additional plugins in the [Oh My Zsh wiki](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins). To enable a new plugin, follow the same steps as for `zsh-autosuggestions`, adding the plugin to your `.zshrc` file.


# Adding a Custom Alias in Oh My Zsh

Customizing Zsh with Oh My Zsh is made easier with the `ZSH_CUSTOM` directory, allowing you to keep your custom configurations separate and organized. Here's how to add a custom alias, such as a `gpush` command for Git operations, with a default message functionality.

## Step 1: Identify the ZSH_CUSTOM Directory

By default, the `ZSH_CUSTOM` directory is located at `~/.oh-my-zsh/custom`. Use this path unless you've customized it.

## Step 2: Create a Custom Aliases File

- **Navigate to Your Custom Directory**: Open a terminal and navigate to your `ZSH_CUSTOM` directory.

```
cd ~/.oh-my-zsh/custom
```

- **Create a New File for Your Aliases**: Separate customizations into their own files for better organization.

```
touch git-aliases.zsh
```

## Step 3: Define Your Custom Alias or Function

- **Edit the New File**: Open the `git-aliases.zsh` file in a text editor.

```
nano git-aliases.zsh
```

- **Add Your Alias or Function**: Insert your custom alias or function. For a dynamic Git push command with a default commit message, use:

```
gpush() {
  # Check if a commit message was provided, default to "Update" if not
  local commit_message="${1:-Update}"
  git add . && git commit -m "$commit_message" && git push
}
```

Save and close the file after adding your customizations.

## Step 4: Apply Your Customizations

Your custom aliases and functions in the `ZSH_CUSTOM` directory will be automatically sourced by Oh My Zsh. To apply your changes immediately, either restart your terminal or source your `.zshrc` file:

```
source ~/.zshrc
```

## Using Your Custom Function

With the `gpush` function in place, you can now use `gpush "Your commit message"` in any of your Git repositories. If no argument is provided, "Update" will be used as the default commit message.

This setup not only enhances your Git workflow with Zsh but also demonstrates the flexibility of Oh My Zsh in customizing your shell experience.
