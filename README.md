Peterson's algorithm is a concurrent programming
algorithm for **mutual exclusion** that allows two
processes to share a single-use resource without
conflict, using only **shared memory** for communication.
It was formulated by **Gary L. Peterson** in **1981**.
The algorithm was later generalized for more than
*two processes*.

Two processes use a respective **flag** to
indicate that they want to enter a critical
section. However using just that could lead to
a deadlock. So they use a tie-breaker **turn** to
indicate whose turn it is to wait. So, each
process says it wants to enter CS but also that
it is its turn to wait. In the end, a process
only waits if the other process wants to enter
CS as well as it is its own turn to wait. This
tie-breaker prevents deadlock.

Java already provides a `ReentrantLock`. This is
for educational purposes only.

> **Course**: [Concurrent Data Structures], Monsoon 2020\
> **Taught by**: Prof. Govindarajulu Regeti

[Concurrent Data Structures]: https://github.com/iiithf/concurrent-data-structures

```java
process(i):
1. I want to enter CS.
2. Its the other process' turn.
3. I wait if you want too and your turn.
4. I enter CS (sleep).
5. I am done with CS.
```

```bash
## OUTPUT
Starting 2 processes (threads) ...
1: want CS
0: want CS
1: in CS0
1: done CS
1: want CS
0: in CS0
0: done CS
0: want CS
1: in CS1
1: done CS
1: want CS
0: in CS1
0: done CS
0: want CS
1: in CS2
1: done CS
1: want CS
0: in CS2
0: done CS
0: want CS
1: in CS3
1: done CS
0: in CS3
0: done CS
```

See [Main.java] for code and [repl.it] for output.

[Main.java]: https://repl.it/@wolfram77/peterson-algorithm#Main.java
[repl.it]: https://peterson-algorithm.wolfram77.repl.run


### references

- [The Art of Multiprocessor Programming :: Maurice Herlihy, Nir Shavit](https://dl.acm.org/doi/book/10.5555/2385452)
- [Myths About the Mutual Exclusion Problem :: G. L. Peterson](https://zoo.cs.yale.edu/classes/cs323/doc/Peterson.pdf)
- [Proof of a Mutual Exclusion Algorithm :: M. Hofri](https://docs.lib.purdue.edu/cgi/viewcontent.cgi?referer=https://www.google.com/&httpsredir=1&article=1778&context=cstech)

![](https://ga-beacon.deno.dev/G-G1E8HNDZYY:v51jklKGTLmC3LAZ4rJbIQ/github.com/javaf/peterson-algorithm)
![](https://ga-beacon.deno.dev/G-G1E8HNDZYY:v51jklKGTLmC3LAZ4rJbIQ/github.com/moocf/peterson-algorithm.java)
