# Mini-Exercise-5

A link to the GitHub repository:
https://github.com/bechornoga/Mini-Exercise-5

Task 3:
The result of the execution of the code is "12482", because each thread out of
the two calls the method "baz()" 10,000 times on the same instance of Foo.
The expected result is "20000".
However, "bar++" is not an atomic operation. It includes reading the value, increasing it, and writing it back. This is a race condition. Since both threads access "bar" at the same time, they can read the same value and overwrite each other's updates.
Therefore, some increments are lost.
As a result, the result is "12482".


Task 4:
In this task, I changed "baz()" and "getBar()" to be "synchronized".
The result of the execution of the code is "20000", because the "synchronized" keyword prevents two threads from entering the synchronized method on the same object at the same time. Therefore, only one thread can execute "baz()" at a time.
Therefore, the threads cannot overwrite each other's updates, and the result is "20000".


Task 5:
In this task, I used a synchronized block inside the "baz()" method.
The variable "bar" is shared by both threads because both threads use the same Foo object.
The block "synchronized(this)" uses the current object as a lock. Since both threads use the same object f, only one thread can enter this synchronized block at a time.
As a result, the increment operation is protected, no updates are lost, and the output is 20000.