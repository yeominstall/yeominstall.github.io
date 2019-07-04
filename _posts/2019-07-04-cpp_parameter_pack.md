---
layout: post
title:  "C++: Parameter Pack"
date:   2019-07-04 08:00:00 +0900
categories: C++
---
# C++: Parameter Pack

Parameter pack은 C++11부터 지원되는 기능으로, 지정되지 않은 갯수(0 or more)의 함수 인자를 받아올 수 있도록 하는 표현식이다.  
C에서만 사용이 가능했던 것 같다.

```c++
// Args ... args

void printWithSpaces(std::string item) {
    std::cout << item;
}

template<typename T, typename... Targs>
void printWithSpaces(std::string item, T value, Targs... args) {
    std::cout << item;
    while (value) {
        std::cout << value << " ";
        printWithSpaces(item.end()+1, args...);
    }
}
```
여러 인자를 받아서 각 인자 사이에 space를 주고 출력하는 함수를 구현하려고 했는데 잘 안 됐다.  
const char*를 이용하는 예제는 많은데 std::string으로 만들고 싶어서 시작했는데 뭐가 문젠지 모르겠다.  


---
**Reference**
1. stackoverflow: variable number of arguments in c++(https://stackoverflow.com/questions/1657883/variable-number-of-arguments-in-c)
2. cppreference.com: parameter pack (https://en.cppreference.com/w/cpp/language/parameter_pack)
3. stroustrup.com: variadic templatesf(http://www.stroustrup.com/C++11FAQ.html#variadic-templates)





