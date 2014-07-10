---
layout: site
title: Projects
---
# Projects

## ejpp

[ejpp](http://chrismanning.github.io/ejpp) is a C++14 wrapper for [EJDB](http://ejdb.org/), a document-store database similar to MongoDB, using BSON as its data and query format.
Unlike MongoDB however, it is used solely as a library from a variety of languages and environments.
ejpp wraps the C API provided by EJDB for a more convenient experience with modern C++.
The main class uses RAII to give automatic exception safety, by way of closing and syncing open databases on destruction.
RAII is also used to provide exception-safe transactions, with usage similar to that of the `mutex` and lock classes of the C++11 standard library and Boost.Thread.
BSON data is consumed and produced as an `std::vector<char>` making it straight-forward for usage with many BSON libraries, including my own jbson.

## jbson

[jbson](http://chrismanning.github.io/jbson) is a BSON and JSON library for C++14.
BSON is a binary data format created for MongoDB and based on the purely textual JSON.
jbson uses template metaprogramming to provide a simple yet flexible API for building BSON data, whether from a Unicode JSON string, or C++ variables; and accessing or modifying existing BSON data.
Though neither depends on the other, jbson can work closely with the above mentioned ejpp, to provide a safe and efficient means to build queries and data, and to interpret data returned from queries or document loads.

Also part of jbson is an implementation of [JSONPath](http://goessner.net/articles/JsonPath/), which functions in a similar manner with JSON (or in this case BSON) as XPath does with XML.
The implementation of JSONPath allows data transformations and even filtering with boolean expressions on BSON data so that complex documents can be more easily digested, and superfluous data ignored.

# University Assignments

The following are projects that were assessed as part of my degree in Computer Science at [De Montfort University](http://www.dmu.ac.uk/).

With thanks to De Montfort University.

## Dynamic Data Structure Visualisation

[ddvs](https://github.com/chrismanning/ddvs) was my final year project.
This was a major project which accounted for a quarter of the total credits gained for my final year grade.

The project is entitled "Dynamic Data Structure Visualisation", its goal being the creation of an educational tool for helping student programmers to grasp the concepts of pointers, memory addresses and data structures, by means of a visual representation of memory.
The approach I had taken involved the implementation of a interpreter for a subset of the C programming language, and to display the interpreter's memory data structures as graphical representations.
This project was my first large project, and also my first use of C++ outside of trivial programs.
Because of this, a huge amount of knowledge and experience was gained in dealing with the flexibility of C++, along with well-known libraries/frameworks Qt and Boost.
The knowledge of how to implement a compiler or interpreter was also attained from scratch and putting it into practice involved much trial and error.
The interpreter is implemented using Boost.Spirit and is actually heavily modified from one of the provided examples; much is built atop the basic design of the original example's design, including `struct`s, pointers and an accompanying simple type system.
Unfortunately, `struct`s were limited to non-recursive data members which severely hampered the goal of the project.
The visualisation was also very limited in both its form and function.
Despite this, the project received a grade of 75%, mostly due to the fact that it was the project management, reports, demonstrations, etc. that were graded and not the quality of the resulting product or code.

While the graphical representation is primitive and the interpreter incomplete, the core approach is perhaps worth revisiting one day to better accomplish the original goal.
See the [final report]({{site.url}}/images/ack_final_report.pdf) for full details.

## nft

[nft](https://github.com/chrismanning/nft) was the result of a university assignment to create a network file transfer application using a socket API and a client-server architecture.
The assignment allowed free choice of programming language, as long as the language had a socket-base network API, and it was then decided to be written in the [D Programming Language](http://dlang.org/).
It takes advantage of D's native and default thread-local storage facilities to avoid most need for explicit synchronisation.
The assignment report can be viewed or downloaded as a PDF from [here]({{ site.url }}/images/nft.pdf), which, in combination with an application demonstration and a brief walk through the code, received a grade of 90%. The code itself was not directly graded.

## Mobile Robots Assignment

[ARIA](http://robots.mobilerobots.com/wiki/ARIA)

See [report]({{site.url}}/images/mobile_robots_report.pdf)
