
Source: Scott Myers: Effective C++

```
Don't use #define for anything other than #ifndef-#define-#endif.

Type-safety and extensibility is the cornerstone of C++.
```

```
printf/scanf are not type-safe. They separate the variables to be read from formatting information. i.e. "%d %x"
is the format specifier and (x, y) are the variables. You have to ensure you provide the right type of variable 
to the right format specifier. In C++, the <</>> operators are overloaded:
cout << i << r;
The  compiler figures out which version of the overloaded function it needs to call for each of i and r.

When doing a scanf, you have to ensure you are taking the address of a variable. i.e. scanf("%d", &i).
If it's a pointer, you only do scanf("%d", ptr). In C++, you have no such worries.
cin >> i;

You can also overload types (extensibility) to read/write class objects:
cin >> class_obj;
cout << class_obj;
```

```
#include<iostream.h> and #include<iostream> are different.
With iostream.h, you get the same elements but at a global scope. This can lead to name conflicts.
This is why you should only use iostream, which gives you the elements within namespace std.
```

```
Don't use malloc or free. They are not constructor/destructor aware.
```

```
Never use "using namespace std;" to include everything in the std namespace to the global
namespace. This can cause naming conflicts.

Here are alternatives:
Declare it in the function using it:

void f()
{
  using namespace std;
  cout << "lol" << endl;
}

OR only import the symbols you need into the global namespace.

using std::cout;
using std::endl;

void f()
{
  cout << "lol" << endl;
}
```
```
Deleting a null pointer in C++ is safe.
int *p = NULL;
delete p;   // does nothing
```
