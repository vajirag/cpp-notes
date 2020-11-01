# Class Templates

## Simple Class Template 
```FixedSizeArray``` template supports different item types.

```c++
template <typename T>
class FixedSizeArray
{
    T data[10] = {0};

public:
    void set(std::size_t index, const T& d) { data[index] = d; }
    T    get(std::size_t index) const { return data[index]; }
};
```

## Specialization for type char
Specialization for type char to provide a different implementation, as an example std::string underlying type is used.

```c++
template <>
class FixedSizeArray<char>
{
    std::string data{10, '#'};

public:
    void set(std::size_t index, char d) { data[index] = d; }
    char get(std::size_t index) const { return data.at(index);}
};
```

## Specialization to limit usage with pointer type
```FixedSizeArray<T*>;``` no implementation is provided, program will not compile if any attempt to use ```FixedSizeArray``` with pointer types.

```c++
template <typename T>
class FixedSizeArray<T*>;
```
