### OOPS

Modern C++ design holds that you should not have getter/setter methods. 
If you want to change the state of a class instance, there are two ways to do this:
* You perform an action on it that mutates its state.
* You create a new instance.

Mutating state via setters is usually a sign of code smell and a bad architectural design.
