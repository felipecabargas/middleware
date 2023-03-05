---
title: 'Setting up a new Mac(Book) for Software Development in 2023'
date: 2023-03-04
draft: false
tags:
  - development
---

![desk](/blog/desk.jpg)

Recently I got a new-and-shiny _M2 Max MacBook Pro_ for my personal use. This was my first time on Apple Silicon since I returned my DTK (_sad, I know_). This meant I needed to move stuff from other computers and install everything again. This gave me the perfect oportunity to learn about new tools, apps and other tips that I think might be useful to you setting up your new devices.

## General settings

- Remove as much as possible from the Dock
- Smaller Dock (by dragging the mouse on the divider at the end)
- True Tone OFF

## macOS Settings & Defaults

Show Library folder

```bash
chflags nohidden ~/Library
```

Change macOS defaults to make sense

```bash
# Show hidden files
defaults write com.apple.finder AppleShowAllFiles YES

# Show path bar in Finder
defaults write com.apple.finder ShowPathbar -bool true

# Show status bar in Finder
defaults write com.apple.finder ShowStatusBar -bool true

# Use jpg for screenshots (smaller size)
defaults write com.apple.screencapture type jpg

# Do not open previously previewed files in Preview
defaults write com.apple.Preview ApplePersistenceIgnoreState YES
```

System Settings

- General
  - Sharing
    - Edit Hostname to whatever you prefer
      - Also you need to run the following:
        ```bash
        sudo scutil --set ComputerName "NAME_GOES_HERE"
        sudo scutil --set LocalHostName "NAME_GOES_HERE"
        sudo scutil --set HostName "NAME_GOES_HERE"
        ```
- Appereance
  - Appereance: Dark
- Accessibility
  - Zoom
    - Use keyboard shorcuts to zoom: ON
- Control Center
  - AirDrop: Show in Menu Bar
  - Bluetooth: Show in Menu Bar
  - Battery
    - Show in Menu Bar: ON
    - Show percentage: ON
  - Keyboard Brightness
    - Show in Control Center: ON
  - Menu Bar Only
    - Clock
      - Display the time with seconds: ON
    - Spotlight: Don't Show in Menu Bar
- Privacy & Security
  - Security
    - Allow apps from App Store and identified developers
  - Firevault
    - Turn ON
- Desktop & Dock
  - Dock
    - Minimize windows using: Scale Effect
    - Automatically hide and show the Dock: ON
    - Show recent applications in Dock: OFF
  - Windows & Apps
    - Default Web Browser: Whatever you prefer
  - Hot Corners
    - Bottom Left: Lock Screen
- Displays
  - Under "Use as": Select "More Space"
  - True Tone: OFF
- Keyboard
  - Text Input > Input Sources > Edit
    - Correct spelling automatically: OFF
    - Capitalise word automatically: OFF
    - Add period with double-space: OFF

## Homebrew

Install Xcode and the command line tools

```brew
xcode-select --install
```

Install [Homebrew](https://brew.sh/)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Applications

#### HomeBrew to the rescue

- Install as much as we can through `brew` (I use `google-chrome` so just switch to `firefox` or another browser if you want)

```bash
brew install --cask \
  google-chrome \
  iterm2 \
  visual-studio-code \
  docker \
  slack \
  obs \
  discord \
  figma \
  imageoptim \
  spotify \
  postgres \
  postico \
  zoom # I don't use zoom but most of ya' do so there you have it
```

- Install console utilities

```bash
brew install \
  git \
  tig \
  tree \
  gnupg \
  gh \
  wget
```

`tig` is a better `git log`

![tig](/blog/tig.png)

`tree` gives us better directory tree views

![tree](/blog/tree.png)

#### More Applications

- Install `oh-my-zsh` (https://ohmyz.sh/)

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- Import your `.zshrc` (or use mine!)

```bash
git clone git@github.com:felipecabargas/dotfiles.git
dotfiles/
cp .zshrc ~/.zshrc
```

Change your theme in `.zshrc` or use `rubyist` (made by yours truly):

![rubyist](/blog/rubyist.png)

```bash
git clone git@github.com:felipecabargas/oh-my-zsh-rubyist-theme.git
ln -ls path/to/rubyist.zsh-theme ~/.oh-my-zsh/themes/rubyist.zsh-theme
```

#### Other Recommended Applications

+ [Hand Mirror](https://apps.apple.com/us/app/hand-mirror/id1502839586/mt=12) - _Freemium_: Preview your webcam on 1-click.
+ [Dropover](https://dropoverapp.com/) - _Freemium_: Drag-n-Drop with Share functionality.
+ [Shottr](https://shottr.cc/) - _Free_: Better screenshots, blur and other tools.
+ [Later](https://getlater.app/) - _Free_: Send all windows to the shadow realm for a bit. By the great [Alyssa X](https://twitter.com/alyssaxuu).
+ [Hidden Bar](https://superbits.co/hidden/) - _Free_: Hide icons on your menu bar.
+ [GoodNotes](https://www.goodnotes.com/) - _Paid_: Note taking, with great iPad support (I take notes with an iPad Mini and Apple Pencil).
+ [AfterShip](https://apps.apple.com/us/app/aftership-package-tracker/id507014023) - _Freemium_: Great package tracking app (install the iPad app linked and login with the same account as your phone!).
+ (I also use NordVPN and the Affinity V2 Suite but any VPN and Image Editing Software would do)
 
#### Things I use and you might not need:

- RVM: follow their [online guide](https://rvm.io/)
- NVM: follow their [online guide](https://github.com/nvm-sh/nvm#installing-and-updating)
- Flutter: `brew install --cask flutter`
- Arduino IDE: `brew install --cask arduino-ide`

## Applications Settings

#### iTerm 2

![iterm](/blog/iterm.png)

- Appereance
  - General
    - Theme: Minimal
- Profiles
  - General
    - Working Directory: Reuse previous' session's directory
  - Color
    - Color Preset: Dark+ (with background changed to #141414)
  - Window
    - Window Appereance
      - Transparency: 15
      - Blur: ON & 7
  - Terminal
    - Scrollback Buffer
      - Unlimited Scrollback: ON

#### Visual Studio Code

I use the built in Settings Sync feature but if you care, this are the important ones:

![vscode](/blog/vscode.png)

- Text size: 12
- Tab size: 2
- Indent using spaces: true
- Icon Theme: Seti
- Color Theme: Dark Lemon Material
- Extensions:
  - Arduino
  - C/C++ (by Microsoft)
  - CMake
  - Dart
  - Flutter
  - Flutter Tree
  - Go
  - Rails
  - Ruby
  - ruby-rubocop
  - Serial Monitor
  - VSCode Ruby
  - vscode-gemfile

Run the "Install 'code' command in PATH" by using the Command Palette inside VSCode.

#### Git

To start changing settings create the `.gitconfig` file

```bash
touch ~/.gitconfig
```

Then open the file in an editor and add the following (replace with your data)

```conf
[user]
  name   = A. Felipe Cabargas
  email  = me@felipe.codes
[github]
  user   = felipecabargas
[init]
	defaultBranch = main
```

## SSH & GPG keys

I was about to write a section on this but GitHub's help center has waaaay better and in detail guides to help you with this. GPG is already installed at this point so you won't run into any issues.

- [Generating a new SSH key and adding it to the SSH agent - GitHub.com](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)

**PLEASE ENABLE COMMIT VERIFICATION ON YOUR GITHUB ACCOUNT (AND 2FA)**

---

I hope this has been helpful for you, and feel free to contact me (email me [me@felipe.codes](mailto:me@felipe.codes)) if you have any questions or suggestions to improve on this!
