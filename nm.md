---
aliases: Name Mangler
---
#todo #Shell 

`nm -C lib.a | less`
Demangles for `C/CPP` the file lib.a. `less` shows one result per page.
The symbols are prefixed with the following letters:

* U (Undefined): referenced in the object file but not defined. Expected to be defined in another object file or library during the linking phase.
* T (Text): Functions and globally accessible variables usually fall into this category.
* t (Local Text): only visible within the object file where it's defined.
* s (Static): The symbol is only accessible/visible within the same file where it's defined.

`ar t lib.a
Archive utility. `t` returns the table of contents. In this case the `.o` files.
#### References
[[ar 1]]
[[Shell Commands 1]]