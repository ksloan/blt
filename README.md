# .blt

.blt is a minimal and flexible file format loosely inspired by the [Bullet Journal Method](https://bulletjournal.com/pages/learn) for those who like to stay organized with simple text files.

This is what it looks like:

<img src="https://ksloan.github.io/blt/custom.png" width="400">

You don't need to install _anything_ to use the .blt file format.

The VS Code extension provides syntax highlighting to make reading, writing, and skimming your files easier. The syntax highlighting work with a few [default themes](#themes), but can be [easily customized](#customize-recommended).

There are no rules to using .blt, but if you're interested, I've included [how I use it at work](#Recommended-Usage-for-Work).

.blt is most powerful when used alongside [whaatch](https://github.com/ksloan/whaatch) and [git lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) to maintain to-the-second traceability.

## More Complex Examples

<img src="https://ksloan.github.io/blt/complex.png" width="500">

## Installation

Right now the .blt extension is still in beta, and unpublished.

To install, first download the `blt.vsix` bundle from []() and, then add it to vscode using one of these two methods:

1. From the command line: `code --install-extension /path/to/blt.vsix`
2. From VS Code GUI: Go to the extensions tab in VS Code, click the ellipsis in the top bar ("..."), and click "Install from VSIX".

Please report any issues to this GitHub repo.

## Theming

### Customize (Recommended)

In order to customize colors, add to the `editor.tokenColorCustomizations` in your settings.json. You can copy the sample config provided here: [sample settings](samples/settings.json).

Example:

```
{
  "scope": "task.complete.blt",
  "settings": {
    "foreground": "#2c3e50"
  }
}
```

### Default Themes

Designed to work with existing VS Code themes (some work better than others).

#### Dark +

<img src="https://ksloan.github.io/blt/dark+.png" width="300">

#### Light +

<img src="https://ksloan.github.io/blt/light+.png" width="300">

#### Solarized

<img src="https://ksloan.github.io/blt/high-contrast.png" width="300">

## Known Issues

1. In order to get the colors to show up as desired with the default themes, the grammar highlighting isn't semantic. (ex. Important items are marked as "invalid.illegal.blt" so they show up in red.) This will cause issues with themes that haven't been tested.
1. It doesn't seem like extending `editor.tokenColorCustomizations`, or themes in general for that matter, is possible with a vscode extension. We could provide a convenience vscode command to update user settings [in the future](https://stackoverflow.com/a/68600738).

## Contributing

The tmLanguage file is generated via https://eeyo.io/iro (see [the .iro file](/iro/blt.iro)] which allows us to compile for various other editors in the future!

Tip for debugging in VSCode: Trigger the scope inspector from the Command Palette with the `Developer: Inspect Editor Tokens and Scopes`.

# Recommended Usage for Work

I've tried many methods over the years, but I've settled into a rhythm with this file structure:

```
LOG.blt
READ.blt
meetings/
    210101 meeting topic.blt
    210102 meeting topic.blt
    ...
recurring/
    person.blt
    teamsync.blt
    ...
```

Every file is a flat list of items.

### Log

`LOG.blt` is the primary file where I prioritize and complete tasks. Completed or delegated items are shuffled (⌥+↑ on Mac) upwards and kept as a record. The remaining open tasks are ranked in order of importance beneath those. I use `# Headers` to delineate un-prioritized tasks into responsibility areas, until they are properly prioritized in my primary list.

An example:

```
x completed task
x completed task
^ pushed off for later: reason or ~date to revisit
> delegated task @user
x recently completed task

. top priority task
o prepare for presentation ~friday
. tertiary task

# Architecture
. update architecture diagrams
. review presentation

# some other topic
. another unprioritized task
```

### Meetings

There are two generally types of meetings (`recurring`, or one-off `meetings`).

For both types, I open the meeting file and jot down items that come up (tasks, inspiration, notes, delegations etc...). After the meeting I'll review and decide if any action items need to be moved from this file to my main LOG.blt file, or somewhere else.

When I delegate a task I mark is as delegated in `LOG.blt` and copy it to the relevant `recurring/person.blt` file where I may take more notes about it, and followup on it at the next meeting.

I use a [date stamp snippet](https://gist.github.com/ksloan/fa3b9be564e1ae0f822bcb0ed43be278) to slap a date in the header of new meeting files (`# 210831`) which then easily get saved using that as the filename afterwards.

### Read

`READ.blt` is just a list of URLs or books I want to get to eventually. This is a great habit to stop yourself from pretending your being productive by consuming content. When I find something interesting I put it in that list, and if it's still interesting later I'll go back and read it. Most of the time it isn't.
