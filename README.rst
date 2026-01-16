cx
==

claude launcher with fuzzy file completion.

starts claude in the background while you type, so it's ready when you
submit.

install
-------

::

   chmod +x cx
   ln -s /path/to/cx ~/.local/bin/cx

requires uv (handles dependencies automatically).

usage
-----

::

   cx [options] [-- claude flags]

built-in options:

``-y, --yolo``
   skip all permission prompts

``-r, --resume``
   resume last conversation

``-h, --help``
   show help

in prompt:

@filename fuzzy-search files in cwd ctrl-g edit in vim ctrl-d submit
ctrl-c cancel ctrl-z suspend (fg to resume)

skills
------

configure custom skills via ``~/.config/cx/config.toml``:

::

   [skills.delegate]
   flag = "d"
   desc = "reader/maker subagents"
   path = "~/.claude/skills/delegate/SKILL.md"

skills appear as flags in ``cx -h`` and inject their content as system
prompts.
