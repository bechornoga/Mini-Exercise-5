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


Task 6:
In this task, I ran the program with 10 threads without using "synchronized".
Each thread calls "baz()" 10,000,000 times.
The expected mathematical result is 100,000,000, because there are 10 threads and each one performs 10,000,000 increments.
However, the actual result is 26001612, because "bar++" is not atomic.
It includes reading the value, incrementing it, and writing it back. Since several threads access "bar" at the same time, some updates are lost.
This is a race condition.
The second number in the output is the running time in milliseconds. In our case, 66 milliseconds.


Task 7:
In this task, I ran the program with 10 threads using a synchronized block inside the
"baz()" method.
The variable "bar" is shared by all of the threads because all of them use the same Foo object.
The block "synchronized(this)" uses the current object as a lock. Since both threads use the same object f, only one thread can enter this synchronized block at a time.
As a result, the increment operation is protected, no updates are lost, and the output is 100000000.
The second number in the output is the running time in milliseconds. In our case, 11017 milliseconds, much longer than the running time of the code in which we did not use synchronized (locks).