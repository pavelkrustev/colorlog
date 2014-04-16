ColorLogs - A PERL script to colorize log viewing, command output etc
---------------------------------------------------------------------

This version - 1.4:

Pavel Krustev - pavelkrustev[]gmail.com
Made the script mobile - no external modules dependences 
and the configuration is included inline and a single file can be copied to many servers with all preferences already set
Useful for environments of similar kind - for example many web or JEE app servers in my case.

Previous version - 1.3:
adapted by Nick Clarke - memorius@gmail.com - http://planproof-fool.blogspot.com/
http://github.com/memorius/colorlogs/

Original version - 1.2:
forked from v1.1 obtained from here, unknown license:
http://www.resentment.org/projects/colorlogs/

This program is free software. It comes without any warranty, to
the extent permitted by applicable law. You can redistribute it
and/or modify it under the terms of the Do What The Fuck You Want
To Public License, Version 2, as published by Sam Hocevar. See
WTFPL.txt for more details.


Requirements
-------------
Requires (obviously) a terminal that understands color escape codes.

Requires perl 5.
No additional perl modules or other file dependences required.


Usage:
------
To use: link colorlogs into your path, e.g.

ln -s ~/src/Colorlogs/colorlogs.pl ~/bin/colorlogs

You may also want to do the same with the 'color-ant' script (see below)

Now to run:

  <some-command-that-writes-stdout> | colorlogs


Customizing the highlighting
----------------------------
Open the perl file itself (colorlogs.pl. Find the array describing all patterns:

    my @config_patterns = (

    'GREEN          regex:\b200\b',				# HTTP prominent errorcodes
    .....

The rules are line-based and fairly self-explanatory,
see example files in 'config/' directory for samples.

The rules are applied in order - the first rule to match a given line is used.
For available colors, see head of colorlogs.pl.


Using in scripts
----------------
The script will try to detect when it is not running in a terminal and will
just pipe its output verbatim if not - so it can still be used in pipelines,
when redirecting output to a file, etc.
