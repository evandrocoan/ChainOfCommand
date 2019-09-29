# Chain of Command

__Sublime text plugin to run a chain of commands__

----------


## Installation

### By Package Control

1. Download & Install `Sublime Text 3` (https://www.sublimetext.com/3)
1. Go to the menu `Tools -> Install Package Control`, then,
   wait few seconds until the `Package Control` installation finishes
1. Go to the menu `Preferences -> Package Control`
1. Type `Package Control Add Channel` on the opened quick panel and press <kbd>Enter</kbd>
1. Then, input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Now, go again to the menu `Preferences -> Package Control`
1. This time type `Package Control Install Package` on the opened quick panel and press <kbd>Enter</kbd>
1. Then, search for `ChainOfCommand` and press <kbd>Enter</kbd>

See also:
1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


### Usage

To run a chain of commands you run the `chain` window commands and pass it a list of commands to run. Each command is defined as a list where the first argument is the name of the command to run and any additional arguments will be
passed directly to the command.

For example, to run the __select_all__ command and then run the __copy__ command you would call:

```python
window.run_command("chain",{"commands":[["select_all"],["copy"]]})
```

Or if you wanted to focus the first group in a window:

```python
 window.run_command("chain",{"commands":[["focus_group",{"group":0}]]})
```

The point is to be able to build custom key bindings to run a sequence of commands. Lets say you wanted a key binding to duplicate the current file. You could set this key binding:

```json
{
  "keys": ["super+shift+option+d"],
  "command": "chain",
  "args": {
    "commands": [
      ["select_all"],
      ["copy"],
      ["new_file"],
      ["paste"],
      ["save"]
    ]
  }
}
```

This would select all the text, copy it, create a new file, paste the text, then open the save file dialog.
