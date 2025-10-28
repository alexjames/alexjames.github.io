When you want to only test your class and not other classes it depends on, you need a way to mock functionality called
by your class. For this, we make use of mock frameworks. In Java, there are two kinds of mock frameworks. Ones that 
use proxy objects and others that use class remapping.

A proxy object is used in place of the real object to imitate the real object.
