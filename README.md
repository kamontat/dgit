# dgit(1) - Version control for designer

- [Setup](#setup)
- [Usage](#usage)
- [Example](#example)
- [Images](#images)
- [Miscellaneous](#miscellaneous)
  - [Install Window](#install-window)
  - [Install Unix](#install-unix)
  - [ZSH Completions](#zsh-completions)
  - [Git](#git)

## Setup

Setup is a little bit hard, please ask developer to set or you also can try by yourself.

1. Install `git` command @[link](https://git-scm.com/downloads) ([more about git](#git))
1. This command require `bash` version 4 or more or `zsh`, I recomment to install latest version.
    1. Window - require **win10** [how-to](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)
    1. Linux - bash is pre-install, so check version and upgrade to latest
    1. MacOS - use [homebrew](https://brew.sh) to install bash [how-to](https://github.com/Toberumono/Miscellaneous/wiki/Installing-Bash-4.3-on-Mac-OSX)
1. If you install zsh, You will able to use zsh-completions, But If a lot hard to setup!
    1. To setup zsh-completion, please follow this [link](#zsh-completions)
1. To **install** script ([window](install-window), [macOS](install-unix), [linux](install-unix))

## Usage

1. Call by full path `/xx/yy/ws action [type] [argument]..`
1. Call by name `ws action [type] [argument]..` (require install)
1. For more information, you can run `ws help`

## Example

1. `ws list all` - list all version and state
1. `ws save version version-1 "finish dark mode"` - create new version with message
1. `ws checkout version-1-light` - move to **version-1-light** version

## Images

<details>
    <summary>Help</summary>

![help](/images/help.png)

</details>

<details>
    <summary>Example usage</summary>

<details>
    <summary>Example list</summary>

![l-all](/images/list-all.png)

![l-state](/images/list-state.png)

![l-version](/images/list-version.png)

</details>

<details>
    <summary>Example save</summary>

![s-state](/images/save-state.png)

![s-version](/images/save-version.png)

</details>

<details>
    <summary>Example checkout</summary>

![checkout](/images/checkout.png)

</details>

</details>

<details>
    <summary>Auto-complete</summary>

![ac-co1](/images/auto-completion-checkout-1.png)

![ac-co2](/images/auto-completion-checkout-2.png)

![ac](/images/auto-completion-main.png)

</details>

## Miscellaneous

### Install Window

don't know!

### Install Unix

1. move `ws` to `/usr/local/bin`
1. make `ws` executable, run `chmod +x /usr/local/bin/ws`

### ZSH Completions

1. move `_ws` to `/usr/local/share/zsh/site-functions`

### Git

**git** is one type of version control which most of developer use it.

1. [more information (en)](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
1. [more information (th)](https://git-scm.com/book/th/v1/เริ่มต้นใช้งาน-เกี่ยวกับ-Version-Control)