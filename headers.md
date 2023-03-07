# Headers

## Adopt a single convention for private header file names

Do use `<name>_private.h` (and `<name>_private.hpp`) in general.  This
must be in the `src/` tree, not in `include/`.

Do not use `<name>_internal.h` or `<name>.h`.

The Proton code uses internal more than private.  The router code uses
private a lot and internal very little.

Question: Why *not* just use `<name>.h` for these, supposing they are
in the `src/` dir?  This is my preference so long as it doesn't cause
collisions or too much confusion.
