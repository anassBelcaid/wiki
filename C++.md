# C++


## Measuring Time

In order to measure time with the new `c++` standard, it'is recommended to use
the **chrono** library.

```cpp
#include <chrono>
```


A static class of this library is the `high_resolution_clock`


So first we need to obtain two instances of these class between the **starting**
and the **finishing** time.


```cpp
auto start  = std::high_resolution_clock::now();

... Run your code

auto finish  = std::high_resolution_clock::now();
```

Once we computed the difference, we could extract the difference with a
`duration` instance. The duration must specify the type and unit.


```cpp
chrono::duration<double, std::milli> diff(end - start);
```

The difference number is stored in the `count` function.

```cpp
double time = diff.count();
```
