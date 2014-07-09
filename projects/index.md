---
layout: site
title: Projects
---
# Projects

## ejpp

[ejpp](http://chrismanning.github.io/ejpp) is a C++14 wrapper for [EJDB](http://ejdb.org/), a document-store database similar to MongoDB, using BSON as its data and query format.
Unlike MongoDB however, it is used solely as a library from a variety of languages and environments.
ejpp wraps the C API provided by EJDB for a more convenient experience with modern C++.
The main class uses RAII to give automatic exception safety, by way of closing on destruction.
RAII is also used to provide exception-safe transactions, with usage similar to that of the `mutex` and lock classes of the C++11 standard library and Boost.Thread.
BSON data is consumed and produced as an `std::vector<char>` making it straight-forward for usage with many BSON libraries, including my own jbson.

## jbson

[jbson](http://chrismanning.github.io/jbson) is a BSON and JSON library for C++14.
BSON is a binary data format created for MongoDB and based on the purely textual JSON.
jbson uses template metaprogramming to provide a simple yet flexible API for building BSON data, whether from a Unicode JSON string, or C++ variables; and accessing or modifying existing BSON data.
Though neither depends on the other, jbson can work closely with the above mentioned ejpp, to provide a safe and efficient means to build queries and data, and to interpret data returned from queries or document loads.

Also part of jbson is an implementation of [JSONPath](http://goessner.net/articles/JsonPath/), which functions in a similar manner to JSON (or in this case BSON) as XPath does to XML.
The implementation of JSONPath allows data transformations and even filtering with boolean expressions on BSON data so that complex documents can be more easily digested, and superfluous data ignored.

## nft

[nft](https://github.com/chrismanning/nft) was the result of a university assignment to create a network file transfer application using a socket API and a client-server architecture.
The assignment allowed free choice of programming language, as long as the language had a socket-base network API, and it was then decided to be written in the [D Programming Language](http://dlang.org/).
It takes advantage of D's native and default thread-local storage facilities to avoid most need for explicit synchronisation.
The assignment report can be viewed or downloaded as a PDF from [here]({{ site.url }}/images/nft.pdf), which, in combination with an application and brief code demonstration, received a grade of 90%. The code itself was not directly graded.

## ddvs

Final year project.
