# MANPATH(3)

## NAME
manpath - return the search path for manual pages

## SYNOPSIS
import **manpath**

String *manpath*.**get_manpath**(Integer *debug_level* = 0, Boolean *quiet_mode* = False)

String *manpath*.**get_locales**(Integer *debug_level* = 0, Boolean *quiet_mode* = False)

## DESCRIPTION
The **get_manpath**() function returns a string of colon separated directories containing manual pages.

The **get_locales**() function returns a string of colon separated locales for which there are localized manual pages.

For each of the two functions, if the optional *debug_level* is set to 1, 2 or 3 it will also print increasingly verbose debugging messages to the console.

And if the optional *quiet_mode* argument is set to True it will discard warning messages printed to the console.

## ENVIRONMENT
The following environment variables affect the execution of **manpath**:

Environment variable | Use
-------------------- | ---
MANLOCALES|If set, causes the utility to override any other configuration found on the system.
MANPATH|If set, causes the utility to override any other configuration found on the system.
PATH|Influences the manual path as described in the IMPLEMENTATION NOTES.

## SEE ALSO
[manpath(1)](https://github.com/HubTou/manpath/blob/main/MANPATH.1.md)

## STANDARDS
The **manpath** library tries to follow the [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guide for [Python](https://www.python.org/) code.

## HISTORY
This library was made for the [PNU project](https://github.com/HubTou/PNU).

## LICENSE
It is available under the [3-clause BSD license](https://opensource.org/licenses/BSD-3-Clause).

## AUTHORS
[Hubert Tournier](https://github.com/HubTou)

