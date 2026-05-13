---
title: "Zero Cost Principle in C++"
date: 2025-03-29
---

<br/><br/>

Modern programming languages use abstraction to help engineers avoid dealing with computer related terms. A list of strings can be handled and thought of as a list of strings rather than a list addresses that we may miuse with the slightest typo. Abstractions relieve the trouble of bugs and make the code more expressive by using concepts from the domain of the application.  

An example of C++ abstractions by comparing the code for the problem: "How many Sarahs are in this list of name".

```C
struct name_node {const char* name_; string_node* next_;};
int count_sarahs(name_node* names){

    int count = 0;
    const char* sarah = "Sarah";
    name_node* query;

    for (n=names; n!=0; n=n->next_){
        if (strcmp(n->name_, sarah)==0){
            count++;
        }
    }
    return count;
}
```

The equivalent C++ code:
```CPP
int count_sarahs(const std::list<std::string>& names) {
  return std::count(books.begin(), books.end(), "Sarah");
}
```

Both the C++ and C code have the same functionality. However the C++ can abstract away computer related terminology such as pointers, for loops and if statements, and handcraft linked lists, etc.

Abstractions is used across all programming langauges, what seperates C++ with most is that it strives to implement these abstractions at zero cost of runtime performance. That does not mean code written in C++ is always faster than code in C#. Rather, programmers have more control of the emitted machine code and memory footprint when needed. Most applications do not need optimal performance. It might make sense to compromise performance with faster compile times, memory safety, and readability, like other programming languages. However, if you work in robotics like I do, sometimes you will have to write code to squeeze every last drop of juice from the harddware. 

Realistically, all abstractions cost something. It can be slower runtime, slower compilation time, hard to read errors. What is more commonly talked about in C++ is Zero Cost Principle. Bjarne Stroustrup, the inventor of C++, defines the zero-overhead principle like this: "What you don’t use, you don’t pay for. And further: What you do use, you couldn’t hand code any better"