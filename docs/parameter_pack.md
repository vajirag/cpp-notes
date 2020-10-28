Parameter pack is simply a sequence of type and value pairs, introduced with C++11 standard.

---

Before diving into parameter pack concept, lets start with basic template specific terminology. In the following example:
```c++
template <typename T>
void my_print(T param)
```

```T``` is a **template parameter** and ```param``` is a **function parameter**.

---

Moving on, you will notice the ellipsis (...) notation in use in next example, which is common in computer programming domain to denote ranges or variable numbers of items.

```c++
template <typename T, typename... Ts>
void join(std::stringstream& ss, T arg, Ts... args)
```

Here, ```typename...``` denotes a variable number of typenames in ```typename... Ts``` template parameter declaration. Therefore, ```Ts``` is not just a template parameter, but a **template parameter pack**.

Similarly, ```Ts...``` denotes variable number of parameter types in ```Ts... args``` function parameter declartion.
Therefore ```args``` is not just a function parameter, but a **function parameter pack**.

---
Next example shows the practical usecase of **parameter pack** with new type of a template called **variadic template**.

In the example, the template function ```join``` accepts variable number of arguments of different types and joins it with the delimitor '|'. For example you can use this function to join any type of argument that supports ```operator<<``` like int, float, string or user-defined type with ```operator<<```.

This template funtion is a new type of a template called **variadic template**. As you can see, a **variadic template** is a  template that accepts variable number of template parameters.

```args...``` expands the parameter pack during the recursive instantiation of template function join.

```c++
#include <gtest/gtest.h>
#include <sstream>


template <typename T>
void join(std::stringstream& ss, T arg) {
    ss << "|" << arg << "|";
}

template <typename T, typename... Ts>
void join(std::stringstream& ss, T arg, Ts... args) {
    ss << "|" << arg;
    concat(ss, args...);
}

TEST(cpp11, variadic_template)
{
    std::stringstream ss;
    join(ss, "Example", 2020, 1.85);

    EXPECT_EQ(ss.str(), "|Example|2020|1.85|");
}
```

---

