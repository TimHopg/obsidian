#todo #C_Language 

MLX or MiniLibX is a windows system [[API]] for C developed in 1984.

Useful functions:
- `mlx_init` - initialises the library, call before anything else
- `mlx_new_windw` - creates new window instance
- `mlx_hook` - registers events
- `mlx_loop` - loops over MLX pointer, triggering each hook in order of registration
- `mlx_xpm_file_to_image` - converts XPM file to MLX image pointer
- `mlx_put_image_to_window` - puts image to screen at given coordinates
- `mlx_destroy_image`: frees image
- `mlx_destroy_window`: frees window instance
- `mlx_destroy_display`: frees MLX

```C
void *mlx;
void *mlx_win;

mlx = mlx_init();
mlx_win = mlx_new_window(mlx, 1920, 1080, "Window Name");
mlx_loop(mlx);
```

#### X11
X11 is a library that is used alongside MLX


#### Events
Mac has only partial support of X11 so X11_mask isn't supported.

```
enum {
	ON_KEYDOWN = 2,
	ON_KEYUP = 3,
	ON_MOUSEDOWN = 4,
	ON_MOUSEUP = 5,
	ON_MOUSEMOVE = 6,
	ON_EXPOSE = 12,
	ON_DESTROY = 17
};
// usage:
mlx_hook(vars.win, ON_DESTROY, 0, close, &vars);
```
| Key | Event |  | Key | Event |
| --- | --- | --- | --- | --- |
| 02 | 
|
#### References
[42 Docs](https://harm-smits.github.io/42docs/libs/minilibx/introduction.html)

_2024-06-17 17:12_
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1OTI4MzcxNDcsLTgzNDcxNDYxNV19
-->