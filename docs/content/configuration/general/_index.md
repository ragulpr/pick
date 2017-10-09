+++
title = "General"
date =  2017-10-09T12:32:22-07:00
weight = 1
+++

## General
The general section controls general settings for pick.

```toml
[general]

[general.password]
# Specifies the length of generated passwords.
length = 25

# Specifies the mode to generate new passwords, currently supported: "interactive".
# If set to "interactive", the password generation can be modified in the following ways:
#  - Increase character set via: Up-arrow key / "k"
#  - Decrease character set via: Down-arrow key / "j"
#  - Increase length via: Right-arrow key / "l"
#  - Decrease length via: Left-arrow key / "h"
#  - Use current password: Enter key
mode = "interactive"
```
