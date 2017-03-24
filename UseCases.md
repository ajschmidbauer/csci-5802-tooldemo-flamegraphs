# Use Cases

# Who are Flame Graphs for?

Flame graphs are for you if you're doing something at scale - website, server, program, whatever. If something is done at a large enough scale, the time spent optimizing and finding inefficiencies will pay dividends in the future at scale too.

## How complete should your code be?

Flame graphs are something you use after you've written the code and have it running. Flame Graphs are not very helpful during design, development, and testing.  By using profilers and tools like Flame Graphs you can develop with the philosophy "code now, optimize later". You never truly know what is actually an optimization during development anyways. Another benefit to this philosophy is if optimization is not a priority during development and design, then "clever" tricks to "speed-up" the program can stay out of the code.

## Environment - Large Infrastructure

// Insert stats about Google, AWS, etc infrastructure cost

// Talk about what a 10% gain in efficiency would do

## Program Types

If you have a web server or service, batch processing system, speed critical system, or anything that has a lot of CPU time - you should try Flame Graph Profiling.

## Code Patterns

If much of your program's work is done by external libraries, it's worth ensuring you're using them efficiently. It's also not far fetched for a library to have an inefficiency that hasn't been revealed until now when the library is being used at the scale your program uses it at. If this is the case, find the libraries inefficiency, fix it, and submit a pull request.

### Common Examples

Some libraries have common patterns where they recommend you use them in a specific way, these include JSON parsers, serialization libraries, string functions, network/communication libraries.

A frequent pattern that appears in inefficiencies is not treating a library object as a resource. Let's suppose you need to get some data, do some work on it, then send the result over the network. The network communication here requires serializing the data. A frequent but inefficient pattern is to construct a new serializer object everytime to accomplish this. You can make many serializers, across instances, threads, and method calls that do mostly the same thing. A better much more efficient solution is to make a static serializer resource.

## Language

There is no catch-all tool for flame graphs yet. There is typically one tool for one (or a small handful of) language. Some languages are easier to profile than others.

The easiest languages at this time to profile are:

* Anything on the JVM
	* Java
	* Scala
	* Clojure
	* Groovy
	* Kotlin
	* JRuby
	* Jython
* Go
* PHP
* 

# Who are Flame Graphs not for?

## Program Types
GUI/Frontend programs that are not widely used and where most of the time is spent waiting on user input.

Small services - optimization has a smaller return when not done at scale. 

## Costs
If running your web service costs an inconsequential annual amount, it's likely not worth your time to profile the service for inefficiencies.

# Reading Flame Graphs - Examples Inefficiencies

These are actually quite simple to read.

// Insert picture

// Talk about picture


# Test Systems

## Good canidates we won't be profiling

### Open-Source Distributed Systems

These would all be great canidates for profiling - they have streaming data, perform pretty hefty computations, and are done at scale. Unfortunately, these all seem to be C++ code. At the present time, C++ code is not easy to profile and generate flame graphs for. It has been done, but the tooling does not seem complete.

The systems we could have profiled here include:

* SETI@home
* Folding@home
* Bitcoin/other distributed block chains

## Systems we can easily profile

* Minecraft servers
	* Written in Java
* Docker
	* Written in Go