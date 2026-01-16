cx is a claude code launcher with fuzzy file completion and background startup

key features:

- starts claude immediately via pexpect while user types prompt
- fuzzy @file completion using git ls-files
- ctrl-g opens vim for multiline editing
- ctrl-d submits, ctrl-z suspends
- configurable skills via ~/.config/cx/config.toml
- bottom toolbar shows startup status
- proper terminal state management around prompt_toolkit

architecture:

- pexpect.spawn() starts claude in pty
- background thread monitors output for "Model:" to detect ready state
- prompt_toolkit handles input with refresh_interval for toolbar updates
- terminal state saved/restored around prompt_toolkit
- skills loaded from toml, injected as --append-system-prompt

config format:

    [skills.name]
    flag = "x"           # short flag (optional)
    long = "name"        # defaults to skill name
    desc = "description"
    path = "~/path/to/SKILL.md"

when modifying:

- test the ctrl-g editor flow (should not auto-submit on exit)
- test ctrl-d submission in multiline mode
- test window resize during interaction
- test cancel with ctrl-c (should terminate child cleanly)
- test ctrl-z suspend and fg resume
- test skill flag conflicts (should warn, built-ins win)
