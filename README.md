# cubic_arcade

Example code for cubic input and improved arcade control. This only supports
symetric funcitons

You can use functab.html to generate a static function.

func_tab may be defined as:
```c
int func_tab[128];
...
changefunc(func_tab, <POWER>);
```
Or as:
```c
const int func_tab[128] = {
<OUTPUT FROM functab.html>
};
```


## Documentation

```c
int func(int *func_tab, int x);
```
Use func to lookup a joystick value [-127, 127] in the function table. func_tab must be initalized before using this function. The value returned is a motor value [-127, 127], the sign of the return value is the same as x.

```c
int *changefunc(int *func_tab, float power);
```
Generates a power function in the table func_tab. Returns func_tab.

```c
int turn(int forward, int turn);
```
Computes arcade drive output value from the `forward` value [-127, 127] and the `turn` value [-127, 127]. Returns motor value [-127, 127]. Tries to maintain maximum speed, full forward is 127.

To compute the left motor, where positive `turn` value means turn right. Use `turn(forward, turn)`

To compute the right motor, use `turn(forward, -turn)`

