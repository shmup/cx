cx is a claude code launcher with fuzzy file completion and background startup

key features:

- starts claude immediately via pexpect while user types prompt
- fuzzy @file completion using git ls-files
- ctrl-g opens vim for multiline editing
- ctrl-d submits (explicit binding for multiline mode)
- bottom toolbar shows startup status
- waits for claude to be ready before sending prompt
- proper terminal state management around prompt_toolkit
- SIGWINCH handling for window resizes
- bracketed paste for multiline prompts

architecture:

- pexpect.spawn() starts claude in pty
- background thread monitors output for "Model:" to detect ready state
- prompt_toolkit handles input with refresh_interval for toolbar updates
- terminal state saved/restored around prompt_toolkit
- buffered startup output displayed before handover

when modifying:

- test the ctrl-g editor flow (should not auto-submit on exit)
- test ctrl-d submission in multiline mode
- test window resize during interaction
- test cancel with ctrl-c (should terminate child cleanly)
- test submitting before claude is ready (should wait)
