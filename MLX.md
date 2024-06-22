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
#### Colours
Colours are displayed in the  TRGB format.
`0xTTRRGGBB`
`T` - transparency
`RGB` - Red/Green/Blue
#### Events
Events are things that happen at runtime that can be detected by the program. Keyboard events, mouse events or window events (like closing, resizing a window etc).

Mac has only partial support of X11 so X11_mask isn't supported:
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
#### X11
X11 is a library that is used alongside MLX.

| Key | Event          |     | Key | Event            |
| --- | -------------- | --- | --- | ---------------- |
| 02  | KeyPress       |     | 14  | NoExpose         |
| 03  | KeyRelease     |     | 15  | VisibilityNotify |
| 04  | ButtonPress    |     | 16  | CreateNotify     |
| 05  | ButtonRelease  |     | 17  | DestroyNotify    |
| 06  | MotionNotify   |     | 18  | UnmapNotify      |
| 07  | EnterNotify    |     | 19  | MapNotify        |
| 08  | LeaveNotify    |     | 20  | MapRequest       |
| 09  | FocusIn        |     | 21  | ReparentNotify   |
| 10  | FocusOut       |     | 22  | ConfigureNotify  |
| 11  | KeymapNotify   |     | 23  | ConfigureRequest |
| 12  | Expose         |     | 24  | GravityNotify    |
| 13  | GraphicsExpose |     | 25  | ResizeRequest    |

[X11 Documentation](https://tronche.com/gui/x/xlib/events/)

Masks are used to limit the keys that each event is mapped to.

| Mask | Description |    | Mask | Description |
| --- | --- | ---  | --- | --- |
| `0L` |  NoEventMask | |  `(1L<<12)` | Button5MotionMask |
| `(1L<<0)` | KeyPressMask | | `(1L<<13)` | ButtonMotionMask |
| `(1L<<1)` | KeyReleaseMask | | `(1L<<14)` | KeymapStateMask |
| `(1L<<2)` | ButtonPressMask | |`(1L<<15)` | ExposureMask |
| `(1L<<3)` | ButtonReleaseMask | | `(1L<<16)` | VisibilityChangeMask |
|`(1L<<4)` | EnterWindowMask | | `(1L<<17)` | StructureNotifyMask |
| `(1L<<5)` | LeaveWindowMask | | `(1L<<18)` | ResizeRedirectMask |
|  `(1L<<6)` | PointerMotionMask | | `(1L<<19)` | SubstructureNotifyMask |
| `(1L<<7)` | PointerMotionHintMask | | `(1L<<20)` | SubstructureRedirectMask |
| `(1L<<8)` | Button1MotionMask| | `(1L<<21)`| FocusChangeMask |
| `(1L<<9)` | Button2MotionMask | | `(1L<<22)` | PropertyChangeMask |
| `(1L<<10)` | Button3MotionMask || `(1L<<23)` | ColormapChangeMask |
| `(1L<<11)` | Button4MotionMask || `(1L<<24)` | OwnerGrabButtonMask |
#### Hooks
Hooks are merely functions that are called when an event is triggered.
_Hooking into events_
You can register to any of the events with a hook registration function.

`void mlx_hook(mlx_win_list_t *win_ptr, int x_event, int x_mask, int (*f)(), void *param)`
Some versions of MLX can't implement mask so no mask will be used regardless of this value.

| Hooking event | code | Prototype|
| --- | --- | ---|
|ON_KEYDOWN | 2 |`int (*f)(int keycode, void *param)`|
|ON_KEYUP* | 3 | `int (*f)(int keycode, void *param)` | 
 | ON_MOUSEDOWN* | 4 | `int (*f)(int button, int x, int y, void *param)` | 
 | ON_MOUSEUP | 5 | `int (*f)(int button, int x, int y, void *param)` | 
 | ON_MOUSEMOVE | 6 | `int (*f)(int x, int y, void *param)` | 
 | ON_EXPOSE* | 12 | `int (*f)(void *param)` | 
 | ON_DESTROY | 17 | `int (*f)(void *param)` | 
_*Has mlx_hook alias._
#### Hooking Aliases
-   `mlx_expose_hook` function is an alias of `mlx_hook` on expose event (`12`).
-   `mlx_key_hook` function is an alias of `mlx_hook` on key up event (`3`).
-   `mlx_mouse_hook` function is an alias of `mlx_hook` on mouse down event (`4`).

#### References
[42 Docs](https://harm-smits.github.io/42docs/libs/minilibx/introduction.html)

_2024-06-17 17:12_
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTc1MTU4MDQ3XX0=
-->