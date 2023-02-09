---
title: Visual Studio Code (VS Code)
---

## In Use

- Too many visual distractions most of the time, and when doing Markdown in particular.
- No color theme has really done the trick so far, always revert to the default light or GitHub light.
- Markdown needs too much tweaking.
  - For example, how to get `inline-code` blocks highlighted?
    - (Better answer: use a color theme that supports it, like the default light theme or the macOS Classic theme)
    - (Answer: install Markdown All in One and they get a black outline, which is hideous but at least it works.)

## Keyboard Shortcuts

[[vscode-vim]]

### Navigation

- `Ctrl Tab` to choose from open files.
- `Ctrl+-` previous edit location.
- `Ctrl+Shift+-` next edit location.

- `Cmd+Shift+;` focus breadcrumbs.
- `Cmd+Shift+.` focus breadcrumbs and open siblings.

## Extensions

- [Markdown notes](https://github.com/kortina/vscode-markdown-notes) - Among other things, shows backlinks ("what links here") in a sidebar panel.

## Appearance, color schemes

What about using two different light colors schemes for day/night, just with different tones / contrasts?

- Night Owl / Light Owl
  - [Creating a VS Code Theme \| CSS-Tricks](https://css-tricks.com/creating-a-vs-code-theme/)
  - Less clutter than most but some of the syntax colors (especially for Markdown) could be tweaked.
    - Even full screen, the dark colros are hard to handle.
- GitHub Theme (Official)
  - [primer/github-vscode-theme: GitHub's VS Code theme](https://github.com/primer/github-vscode-theme)
  - Best overall so far...
- Base2Tone - Morning light
  - Some things could use more contrast, for example the status bar text, the terminal command line text
- Base 16 - London Tube - Clean and sane code colors - Red for Markdown lists (like this one). Not going to fly.
- Github Plus
  - White-on-white for "&" in URLs. Looks like an error at first glance but it's also separating query paramters and making them easier to read.
- Github Light Theme
  - [chuling/vscode-theme-github-light: Try this light theme if others don't meet your needs.](https://github.com/chuling/vscode-theme-github-light)
  - Nice and flat.
  - Markdown lists get a light brown color, very bad.
- Winter is Coming
  - [johnpapa/vscode-winteriscoming: Dark theme with fun and bright foreground colors](https://github.com/johnpapa)
  - The light option is not bad, but needs some tweaking. Too much blue text.
- Eva
  - [fisheva/Eva-Theme: A colorful and semantic coloring code theme meet VSCode.](https://github.com/fisheva/Eva-Theme)
  - too colorfull
- Flat UI
  - The "Immersive" options is nice because it looks less cluttered but the default colors aren't great.
- Slack theme
  - [slack-theme/visual-studio-code: Slack Theme for Visual Studio Code](https://github.com/slack-theme/visual-studio-code)
  - The code editor colors are nice, the UI colors feel buggy. For example, in Ochin, disabled extensions in search results are black on dark blue.
    - The darker colors for the sidebar and status bar make the editor area feel less cluttered
- Tokyo Night
  - The dark version is a good start
  - The code editor colors are nice, the UI colors feel buggy. For example, in Ochin, disabled extensions in search results are black on dark blue. - The darker colors for the sidebar and status bar make the editor area feel less cluttered
- Brackets
  - Could tone down the orange. Otherwise pretty good.
- NetBeans Light Theme
  - [obrejla/vscode-netbeans-light-theme: NetBeans Light default theme for Visual Studio Code.](https://github.com/obrejla/vscode-netbeans-light-theme)
  - HTML looks like a traffic light.
- Ysgrifennwr
  - [xaverh/theme-ysgrifennwr: A light colorscheme for Visual Studio Code](https://github.com/xaverh/theme-ysgrifennwr) - Surprisignly good.
- Tokyo Night
  - [enkia/tokyo-night-vscode-theme: A clean, dark Visual Studio Code theme that celebrates the lights of Downtown Tokyo at night.](https://github.com/enkia/tokyo-night-vscode-theme)
  - Nice low-contrast light mode
- Min
  - [misolori/min-theme: A minimal theme for Visual Studio Code](https://github.com/misolori/min-theme)
  - Promising. - Light grey is a bit too light grey. For example in comments and tabs etc. - Also inline code when editing Markdown
- Hop Light - [bubersson/hop-theme-vscode: Theme for Visual Studio Code](https://github.com/bubersson/hop-theme-vscode) - Looks like it only changes code colors, not UI colors.
- Particle Workbench
  - [Workbench Themes - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=particle.particle-vscode-theme)
  - Another favorite
- Quiet Light
  - [onecrayon/theme-quietlight-vsc: Light, peaceful coding for Visual Studio Code](https://github.com/onecrayon/theme-quietlight-vsc)
  - Nice soft theme with a gray background.
  - Too much color in Markdown mode, for example in links.
  - Does something bad with the activity bar
- Horla
  - Not bad?
- Monokai light
  - Nice idea, but needs tweaking for Markdown
- Kay Theme
  - Low contrast, soft. Cutesy.

## Usage

### Writing "prose"

- Spell checking?
- Narrow column?
- Centered text?
- More leading?

### Regular expressions

According to [this SO thread](https://stackoverflow.com/a/42184299), VS Code uses two different regex engines:

- Find in Files (opens in the sidebar) uses Rust regex:
  - [regex - Rust](https://docs.rs/regex/0.2.10/regex/)
- Find (opens in the editor view) uses JavaScript regex:
  - [Regular expressions - JavaScript \| MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
  - [ECMAScript Language Specification - ECMA-262 Edition 5.1](https://www.ecma-international.org/ecma-262/5.1/)
