# MANPATH(1)

## NAME
manpath - display search path for manual pages

## SYNOPSIS
**manpath**
\[-Ldq\]
\[--debug\]
\[--help|-?\]
\[--version\]
\[--\]

## DESCRIPTION
The **manpath** utility determines the user's manual search path from the user's PATH, and local configuration files.
This result is echoed to the standard output.

### OPTIONS
Options | Use
------- | ---
-L|Output manual locales list instead of the manual path.
-d|Print extra debugging information.
-q|Suppresses warning messages.
--debug|Enable debug mode
--help\|-?|Print usage and a short help message and exit
--version|Print version and exit
--|Options processing terminator

## IMPLEMENTATION NOTES
The **manpath** utility constructs the manual path from three sources:
1. From each component of the user's PATH for the first of:
   - pathname/man
   - pathname/MAN
   - If pathname ends with /bin: pathname/../share/man and pathname/../man
2. From default manpath entries:
   - /usr/share/man
   - /usr/share/openssl/man
   - /usr/local/share/man
   - /usr/local/man
3. The configuration files listed in the FILES section for MANPATH entries.
   The information from these locations is then concatenated together.
   If the *-L* flag is set, the **manpath** utility will search the configuration files listed in the FILES section for MANLOCALE entries.

## ENVIRONMENT
The following environment variables affect the execution of **manpath**:

Environment variable | Use
-------------------- | ---
MANLOCALES|If set with the *-L* flag, causes the utility to display a warning and the value, overriding any other configuration found on the system.
MANPATH|If set, causes the utility to display a warning and the value, overriding any other configuration found on the system.
PATH|Influences the manual path as described in the IMPLEMENTATION NOTES.

The *MANPATH_DEBUG* environment variable can also be set to any value to enable debug mode.

The *FLAVOUR* or *MANPATH_FLAVOUR* environment variables can be set to one of the following values, to implement only the corresponding options and behaviours:
* bsd | bsd:freebsd : FreeBSD [manpath(1)](https://www.freebsd.org/cgi/man.cgi?query=manpath)

## FILES
* /etc/man.conf : System configuration file.
* /usr/local/etc/man.d/*.conf : Local configuration files.

## EXIT STATUS
The **manpath** utility exits 0 on success, and >0 if an error occurs.

## SEE ALSO
[apropos(1)](https://www.freebsd.org/cgi/man.cgi?query=apropos),
[man(1)](https://www.freebsd.org/cgi/man.cgi?query=man),
[whatis(1)](https://www.freebsd.org/cgi/man.cgi?query=whatis),
[man.conf(5)](https://www.freebsd.org/cgi/man.cgi?query=man.conf),
[manpath(3)](https://github.com/HubTou/manpath/blob/main/MANPATH.3.md)

## STANDARDS
The **manpath** utility is a standard UNIX command, though not a POSIX one.

This re-implementation tries to follow the [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guide for [Python](https://www.python.org/) code.

## PORTABILITY
To be tested under Windows.

## HISTORY
This re-implementation was made for the [PNU project](https://github.com/HubTou/PNU).

## LICENSE
It is available under the [3-clause BSD license](https://opensource.org/licenses/BSD-3-Clause).

## AUTHORS
[Hubert Tournier](https://github.com/HubTou)

The manpath(1) manual page is mainly based on the one written for [FreeBSD](https://www.freebsd.org/) by [Gordon Tetlow](https://github.com/tetlowgm).

## BUGS
This re-implementation corrects 3 (minor) bugs or the original command:
* No warning was displayed when MANPATH was set
* Default manpath entries were supplied when PATH was not set, before "Adding default manpath entries"
* A "Skipping duplicate manpath entry" message was incorrectly displayed with MANPATH directives with empty content in config files

