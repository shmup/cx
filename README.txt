cx - claude launcher with fuzzy file completion

starts claude in the background while you type, so it's ready when you submit.

usage: cx [options] [-- claude flags]

options:
  -d, --delegate   delegate mode (reader/maker subagents)
  -y, --yolo       skip all permission prompts
  -r, --resume     resume last conversation
  -h, --help       show help

in prompt:
  @filename        fuzzy-search files in cwd
  ctrl-g           edit in vim
  ctrl-d           submit
  ctrl-c           cancel

the bottom toolbar shows claude's startup status:
  - "claude starting..." while loading
  - "claude ready" when ready for input

if you submit before claude is ready, it waits automatically.

dependencies: prompt_toolkit, pexpect (handled by uv)

install:
  chmod +x cx
  ln -s ~/projects/cx/cx ~/.local/bin/cx
