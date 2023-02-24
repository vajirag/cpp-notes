# Constexpr

A constexpr expression tells the compilar to evaluate it at compile time.

A constexpr function tells compilar to evaluate at compile time if all the conditions satisfied for compile time evaluation.

```c++
constexpr pi = 22 / 7;

constexpr double calculate_area(double r) {
    constexpr area = pi * r * r;
    return area;
}
```

Here, constexpr function ```calculate_area``` is invoked using constant expression arguments, therefore ```calculate_area``` guarenteed to be executed at compile time.
