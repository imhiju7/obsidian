
- dùng với [[set]]
```cpp
#include <iostream>
#include <set>

int main() {
    std::set<int> s = {1, 2, 3, 4, 5}; // Example set initialization
    for (std::set<int>::iterator it = s.begin(); it != s.end(); ++it) {
        std::cout << *it << " ";
    }
    return 0;
}

```
- dùng với [[map]]
```cpp
#include <iostream>
#include <map>

int main() {
    std::map<int,int> s = {{3,5}, {2,4}, {3,7}, {6,4}, {7,3}};
    for (std::map<int,int>::iterator it = s.begin(); it != s.end(); ++it) {
        std::cout << (*it).first << " " << (*it).second<<std::endl;
    }
    return 0;
}
```