---
layout: default
title: Frequency Map
parent: Problems
grand_parent: Computer Science
has_children: false
nav_order: 3
permalink: /cs/problems/freq_map/
---
Date: 16 Oct 2022

# Frequency Map
Frequency of each character in a String

## Approach
* Traverse each of the character in the String
* Check whether the current character is present in the Map
* If present the update the frequency else insert in the Map;

Example:

```cpp
    // C++
    string s = "abccccdd";
    
    for (char c : s)
        map[c]++;
```

```java
    // Java
    String s = "abccccdd";
    
    for (char c : s.toCharArray())
        map.merge(c, 1, Integer::sum);        
```
### C++ naive

```cpp
    #include <iostream>
    #include <unordered_map>
    using namespace std;

    int main() {
        string s = "abccccdd";
        unordered_map<char, int> map;

        for (int i = 0; i < s.length(); i++){
            if (map.find(s[i]) == map.end())
                map.insert(make_pair(s[i], 1);
            else
                map[s[i]]++;
        }

        // print
        for (auto& it : map) {
            cout << it.first << ' ' << it.second << '\n';
        }
        return 0;
    }
```

### C++ elegant ;-)

```cpp
    #include <iostream>
    #include <unordered_map>
    using namespace std;

    int main() {
        string s = "abccccdd";
        unordered_map<char, int> map;

        for (char c : s)
            map[c]++;

        // print
        for (auto& it : map) {
            cout << it.first << ' ' << it.second << '\n';
        }
        return 0;
    }
```

### <= Java7 naive

```java
    import java.util.Map;
    public class Main {
        public static void main(String[] args) {
            String s = "abccccdd";
            Map<Character, Integer> map = new HashMap<>();
            for (int i = 0; i < s.length(); i++) {
                if (map.containsKey(s.charAt(i))) {
                    map.put(s.charAt(i), map.get(s.charAt(i)) + 1);
                } else {
                    map.put(s.charAt(i), 1);
                }
            }

            // print
            for (Map.Entry e : map.entrySet()) {
                System.out.println(e.getKey() + " " + e.getValue());
            }
        }
    }
```

### Java 8+ elegant ;-)

```java
    import java.util.Map;
    import java.util.HashMap;
    public class Main {
        public static void main(String[] args) {
            String s = "abccccdd";
            Map<Character, Integer> map = new HashMap<>();

            for (char c : s.toCharArray())
                map.merge(c, 1, Integer::sum);

            // print
            for (Map.Entry e : map.entrySet())
                System.out.println(e.getKey() + " " + e.getValue());
        }
    }
```

