# *rainbow-bash-prompt*

**rainbow-bash-prompt** makes your bash prompt rainbow by using [dosentmatter/lolcat](https://github.com/dosentmatter/lolcat).

[![demo](https://asciinema.org/a/b5hasvkj9mgoho5ntodffabn0.png)](https://asciinema.org/a/b5hasvkj9mgoho5ntodffabn0?autoplay=1)

## Installation

*Tested on macOS Sierra (Terminal and iTerm2) and Ubuntu (GNOME Terminal)*

1. bash must be compiled with readline.
2. Install C implementation of [dosentmatter/lolcat](https://github.com/dosentmatter/lolcat) for speed.
   - That is a fork of [jaseg/lolcat](https://github.com/jaseg/lolcat) with a minor change to make the colors pseudo random.
   - Put the binary in your `$PATH` and name it `lolcat-c`
3. copy `.bash_prompt` to your `$HOME` directory
4. Add this to your `.bashrc`:
~~~~
if [[ -f ~/.bash_prompt ]]; then
  . ~/.bash_prompt
fi
~~~~

## Use

- You can turn on and off debugging by setting `PS1_DEBUG` to `'true'` or `'false'`. Debugging is used to show the non-printing characters and highlight them. It has a line wrap issue as shown in the asciinema recording above that seems to be caused by colored prompts that are too long. This is not an issue because it is only meant for debugging.
- You can change the command used to colorize `PS1` by setting `PS1_COLORIZE_COMMAND` to a name of a function.
  - Currently, it is set to `'__ps1_lolcat'` which uses `lolcat-c` for speed.
  - If you have [rbenv](https://github.com/rbenv/rbenv) with ruby [busyloop/lolcat](https://github.com/busyloop/lolcat) or [pyenv](https://github.com/yyuu/pyenv) with python [tehmaze/lolcat](https://github.com/tehmaze/lolcat) installed, you can set `PS1_COLORIZE_COMMAND` to `'__ps1_lolcat_ruby'` or `'__ps1_lolcat_python'`
- You can change the command used to format the debug output by setting `PS1_DEBUG_COMMAND` to a name of a function.
  - Currently, it is set to `__ps1_debug` which displays non-printing characters and colors them.
  
## Caveats

To have double quotes `"` and backslashes `\` work in both regular and debug mode, PS1 has to have `\\"` and `\\\\` respectively to have the right number of escapes for both modes.
