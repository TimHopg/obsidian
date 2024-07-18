#todo #School42 #C_Language 

This project uses [[MLX]] which is a wrapper for the X11 library. However complicated MLX seems X11 is even more of a headache.

For when I was developing at home on my mac, I used the Remote SSH extension for the first time. And SSH using terminal too to use my familiar dev environment

`keysym` is more abstract than `keycode` so makes your code more portable. The same keystrokes will be registered on Linux and Mac OSX systems.
`X11/keysym.h`
`keycode` is hardware specific. Program instead with `keysym` for more portable code.

`destroy_display` is necessary on Linux architecture (after `destroy_window`). And `free(mlx.ptr)` too.
#### Initialise Data
Initialising data using `ft_bzero()` or `ft_calloc()` is a good way to ensure no variables are used uninitialised. 
#### Structs
It's a good idea to keep all (or the majority) of game data in one struct for management reasons. I recommend using a `tab` or `point` struct which stores an `x` and `y` coordinate field. This way you can pass different `tab` structs to the same functions that will manipulate the coordinate data. 
* Map size
* Enemy location
* Exit Location
* etc.
#### Memory Management
Implement this as you go. It becomes complicated if you try and do it afterwards. There will be several points where different memory needs to be freed. Functions that check for the existence of a variable before freeing will help ensure no attempt is made to free memory that hasn't yet been allocated.
#### Fill Function
Recursively checks each position from each reachable position. Changes the current position to a `*` so a sort of breadcrumb can be left.
#### XPM Files
These are human readable text interpretations of images. A legend of characters and their RGB information is included. It is usually in black to white order.
#### Transparency
Transparency or pixels set to `None` does not work on some MLX systems. To get around this, images can be written pixel by pixel to a 'master image' using a custom pixel put function. In this function, `None` pixels can be skipped.
#### Bonus
Used [[rand()]] with `srand(time(0))` to get enemy to move randomly. `rand()` alone is pseudorandom and will always move the same sequence each time the program is run. It needs a seed from `srand()` which takes a prompt from the `time()` function to be more legitimately random.
#### Extras
Remember to `make re` when changing certain aspects of the program. Especially in header files.
Move function could be refactored to handle enemy and player.
#### References
[Harm Smits 42 Docs](https://harm-smits.github.io/42docs/libs/minilibx/introduction.html)
[42 Cursus Gitbook](https://42-cursus.gitbook.io/guide/rank-02/so_long/understand-so_long)
[Reactive.so Guide](https://reactive.so/post/42-a-comprehensive-guide-to-so_long)
[[Data Alignment]]
[Transparency](https://pulgamecanica.herokuapp.com/posts/mlx-transparency)
[[rand()]]

_2024-06-17 17:11_