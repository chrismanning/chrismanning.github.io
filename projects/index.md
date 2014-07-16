---
layout: site
title: Projects
---

<style>
    #toc {
        width: auto;
        display: inline-block;
        float: right;
        margin: 10px;
    }
    @media (max-width: 48em) {
        #toc {
            float: none;
            margin: 0;
        }
    }
</style>
<div class="pure-menu pure-menu-open" id="toc">
    <ul>
        <li><a class="pure-menu-heading" href="#projects">Personal Projects</a></li>
        <li><a href="#ejpp">ejpp</a></li>
        <li><a href="#jbson">jbson</a></li>
        <li><a href="#executors">Executors</a></li>
        <li><a href="#melo">Melosic</a></li>
        <li><a class="pure-menu-heading" href="#uni">University Projects</a></li>
        <li><a href="#ddvs">Dynamic Data Structure Visualisation</a></li>
        <li><a href="#nft">nft</a></li>
        <li><a href="#robotics">Mobile Robotics Assignment</a></li>
    </ul>
</div>

# <a name="projects"></a>Personal Projects

## <a name="ejpp"></a>ejpp

[ejpp](http://chrismanning.github.io/ejpp) is a C++14 wrapper for [EJDB](http://ejdb.org/), a document-store database similar to MongoDB, using BSON as its data and query format.
Unlike MongoDB however, it is used solely as a library from a variety of languages and environments.
ejpp wraps the C API provided by EJDB for a more convenient experience with modern C++.
The main class uses RAII to give automatic exception safety, by way of closing and syncing open databases on destruction.
RAII is also used to provide exception-safe transactions, with usage similar to that of the `mutex` and lock classes of the C++11 standard library and Boost.Thread.
BSON data is consumed and produced as an `std::vector<char>` making it straight-forward for usage with many BSON libraries, including my own [jbson](#jbson).

## <a name="jbson"></a>jbson

[jbson](http://chrismanning.github.io/jbson) is a BSON and JSON library for C++14.
BSON is a binary data format created for MongoDB and based on the purely textual JSON.
jbson uses template metaprogramming to provide a simple yet flexible API for building BSON data, whether from a Unicode JSON string, or C++ variables; and accessing or modifying existing BSON data.
Though neither depends on the other, jbson can work closely with the above mentioned ejpp, to provide a safe and efficient means to build queries and data, and to interpret data returned from queries or document loads.

Also part of jbson is an implementation of [JSONPath](http://goessner.net/articles/JsonPath/), which functions in a similar manner with JSON (or in this case BSON) as XPath does with XML.
The implementation of JSONPath allows data transformations and even filtering with boolean expressions on BSON data so that complex documents can be more easily digested, and superfluous data ignored.

## <a name="executors"></a>Executors

[Executors](https://github.com/chrismanning/executors) is a C++ experiment to test some of the ideas in the now obsolete (post-Rapperswil) C++ standard proposals: N3562, N3731, N3785, N4032.
This library includes `thread_pool`, a configurable `basic_loop_executor` and default alias `loop_executor`, and a `default_executor` which is simply an accessor to a static `thread_pool`.
These classes do not use virtual functions, and are able to accept move-only types such as `packaged_task` as work.

## <a name="melo"></a>Melosic

Melosic is an unreleased music player that I have created over a period of several years.
All of the above projects are used within Melosic and were once a part of it in some capacity.
Melosic has many features expected of a music player: playlists, library, gapless playback, drag & drop, plugins, etc.
What sets it apart is its extensibility and configurability via C++ plugins, JSON configuration files, and Qt Quick/QML; the latter is available due to its usage of Qt Quick for its user interface, though this is not connected at all to the main program logic allowing use of alternate user interfaces such as Win32, GTK+, Cocoa, curses, etc.

The plugin APIs are simple, yet capable ways to either add something to the existing systems (eg. output devices, input formats), or to "listen" for certain events to provide an auxiliary service (eg. Last.fm scrobbling, song info fetching).
This is achieved by a thread-safe mechanism similar to Qt's signals & slots system, though without the need for an additional preprocessor. These signals can utilise `shared_ptr`s & `weak_ptr`s to provide automatic disconnection of a member function (or any other that throws `bad_weak_ptr`) when an object has expired.

Audio output is done via a custom [Asio](http://think-async.com/Asio) (aka Boost.Asio) interface, which allows both synchronous and asynchronous usage for low latency I/O.
The music library is implemented using [EJDB](http://ejdb.org/) and [ejpp](#ejpp).
Using JSON (or BSON) with ejpp is a huge improvement to usability as it allows easy query declarations in QML (or directly in C++) so that the library can be browsed precisely how a user desires.

# <a name="uni"></a>University Assignments

The following are projects that were assessed as part of my degree in Computer Science at [De Montfort University](http://www.dmu.ac.uk/).

With thanks to De Montfort University.

## <a name="ddvs"></a>Dynamic Data Structure Visualisation

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

While the graphical representation is primitive and the interpreter incomplete, the core approach is perhaps worth revisiting one day to better accomplish the original goal.
See the [final report]({{site.url}}/images/ack_final_report.pdf) for full details.

## <a name="nft"></a>nft

[nft](https://github.com/chrismanning/nft) was the result of a university assignment to create a network file transfer application using a socket API and a client-server architecture.
The assignment allowed free choice of programming language, as long as the language had a socket-base network API, and it was then decided to be written in the [D Programming Language](http://dlang.org/).
It takes advantage of D's native and default thread-local storage facilities to avoid most need for explicit synchronisation.
The assignment report, which was submitted along with an application demonstration and a brief walk through the code, can be viewed or downloaded as a PDF from [here]({{ site.url }}/images/nft.pdf). The code itself was not directly graded.

## <a name="robotics"></a>Mobile Robotics Assignment

The assignment for the Mobile Robotics module was to create a controller for a particular type of robot using [ARIA](http://robots.mobilerobots.com/wiki/ARIA).
My submission provided the following behaviours using a subsumption architecture: obstacle avoidance, edge following, wandering, and mapping.
Also include was a Qt client for graphically viewing a map as it was assembled. See [code]({{ site.url }}/images/mobile_robots_assignment.zip).

See the [report]({{site.url}}/images/mobile_robots_report.pdf) for full details.
