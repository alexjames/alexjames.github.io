#### Comparison of C++ and Java

Input/Output:

###### C++
```
#include <iostream>

int main(int argc, char *argv[])
{
	std::cout << "Lol! This is great!" << std::endl;
	return 0;
}
```
###### Java
```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Lol! This is great!");
    }

}
```

Basic Class definition:
###### C++
Stack allocation and pointer based memory allocation.
```
class MyClass
{
	public:
	int my_x;

	void setx(int x)
	{
		my_x = x;
	}
};

int main(int argc, char *argv[])
{
	MyClass newobjclass;
	std::cout << newobjclass.my_x;

	MyClass *newptrclass = new MyClass();
	std::cout << newptrclass->my_x;

	return 0;
}
```
###### Java
```
MyClass.java:
class MyClass
{
	int my_x;
	
	void setx(int x)
	{
		my_x = x;
	}
}


HelloWorld.java
public class HelloWorld {
    public static void main(String[] args)
    {
	    MyClass newclass = new MyClass();
	    newclass.my_x = 5;
	    System.out.println(newclass.my_x);
    }
}

```

Inheritance:
###### C++
```
class MountainBike : public Bicycle {

    // new fields and methods defining 
    // a mountain bike would go here

}
```


###### Java
```
class MountainBike extends Bicycle {

    // new fields and methods defining 
    // a mountain bike would go here

}
```
