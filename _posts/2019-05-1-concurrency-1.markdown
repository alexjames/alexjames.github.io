---
layout: default
title:  "Concurrency for the Brave: Part 1"
date:   2016-02-12 12:50:00
categories: cs
---

## Why Concurrency
"If one worker can build a house in 30 days, how do you get the same house build in 3 days?"
As your 5th grade math teacher will tell you, the more the number of workers, the sooner you can have that house built. When you have more workers, more tasks get done in parallel, saving time. Multi-core processors are the norm today. We’ve hit the limit on how efficiently we can bump up the clock speed of a single-core silicon-based processor. Hardware engineers have managed to move beyond this limit by throwing in more cores into the mix. While this has solved some problems, it’s created a lot more.

## More Isn’t Better
Writing good multi-threaded programs has become imperative to get the most out of modern microprocessors. The caveat here is that concurrency is hard. This is one of the reasons it’s challenging to write many kinds of low-level systems and distributed systems programs. Concurrency is hard to reason about correctly. A lot of the time instead of writing faster programs, you write programs that are slower, more complex and plain in-correct! They are plagued by subtle, unforseen bugs that are hard to catch and debug. It’s hard to come up with a mental model to analyze and understand them.
I’ve spent a good chunk of my time trying to learn and understand concurrency. A lot of the articles and textbooks I’ve read on the subject didn’t really help me comprehend the subject. I’ve found myself staring at the examples for hours at times without having a clue as to what was going on. It can seem like the dark arts at times and make your head hurt. In this series of articles, I’ll try to summarize everything I’ve learned so far and present a mental framework that I found useful in writing (and debugging) multi-threaded code. Your head is probably still going to hurt. But hopefully, it will seem less intimidating. We will assume uni-core processors, because it’s easier to reason about those at first. The same principles carry over to truly parallel programs on multi-core environments.

## Hanging By A Thread
Every thread executes a series of instructions. They usually perform a series of related but independent tasks within the program. Since we are only looking at the single processor case, only one instruction can execute at any given point in time.
A program called a scheduler picks a thread and gets it to execute on the processor. The scheduler makes decisions such as what thread to run, when and for how long. It may swap a thread for another whenever it likes. As far as the thread is concerned, it should have no awareness of this swap happening and remain in its dreamworld of being the only piece of code executing on the hardware. 
Hardware instructions are usually “atomic”, which is to say that when an instruction is executed, it is completely executed. The scheduler cannot interrupt the processor while it is performing an atomic instruction. It may only interrupt the processor before or after the instruction is executed. In our examples, we will assume all our primitive operations are atomic operations. 

Let’s take a hypothetical processor with a `print` instruction that outputs a string to the console. The pint instruction is atomic and you will never have half of a letter printed to the screen. Let’s say you wrote a program that has three threads which print the characters “A”, “B” and “C” respectively. 
Thread A print “A”
Thread B print “B”
Thread C print “C”
When you execute this program, the order in which instructions execute is completely up to the scheduler. For instance, when you run the program, the output may be: A B C. But it may also output B C A or C A B. There are no guarantees about the order of execution of instructions among threads and a programmer should never make any assumptions about it. Any interleaving of instructions is possible.
Execution traces are used to depict possible orderings of instructions. They are useful in analyzing concurrent patterns. Columns contain the set of instructions that belong to a thread. Rows are ordered from top to bottom and show which instruction was executed at that point in time.  Here is an execution trace for our example:
In this trace, Thread A executed first and printed the character “A”. The scheduler then switched to Thread B which printed “B” on-screen. Finally, the scheduler moved to Thread C, which output “C”.
Here is a trace for the output CAB.

## Your Scheduler Does Not Love You
As long as you have a set of completely independent, mutually-exclusive tasks with no dependencies, you can spin up as many threads as tasks and assign a thread to each one. They should all complete on their own and you don’t have to worry about how the instructions are interleaved during the execution. Reality is less kind.

