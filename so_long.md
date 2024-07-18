#todo #School42 #C_Language 

This project uses [[MLX]] which is a wrapper for the X11 library. However complicated MLX seems X11 is even more of a headache.

For when I was developing at home on my mac, I used the Remote SSH extension for the first time. And SSH using terminal too to use my familiar dev environment

`keysym` is more abstract than `keycode` so makes your code more portable. The same keystrokes will be registered on Linux and Mac OSX systems.
`X11/keysym.h`
`keycode` is hardware specific. Program instead with `keysym` for more portable code.

`destroy_display` is necessary on Linux architecture (after `destroy_window`). And `free(mlx.ptr)` too.
#### Initialise Data
Initialising data using `ft_bzero()` or `ft_calloc()` is a good way to ensure no variables are used uninitialised. 
#### Memory Management
Implement this as you go. It becomes complicated if you try and do it afterwards. There will be several points where different memory needs to be freed. Functions that check for the existence of a variable before freeing will help ensure no attempt is made to free memory that hasn't yet been allocated.

#### Bonus
Used [[rand()]] with `srand(time(0))` to get enemy to move 
#### References
[Harm Smits 42 Docs](https://harm-smits.github.io/42docs/libs/minilibx/introduction.html)
[42 Cursus Gitbook](https://42-cursus.gitbook.io/guide/rank-02/so_long/understand-so_long)
[Reactive.so Guide](https://reactive.so/post/42-a-comprehensive-guide-to-so_long)
[[Data Alignment]]
[Transparency](https://pulgamecanica.herokuapp.com/posts/mlx-transparency)
[[rand()]]

_2024-06-17 17:11_