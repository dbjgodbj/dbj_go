---
title: "Is this progress?"
date: 2019-05-15
description: "Example of a C++ ever-adding complexity"
tags: ["basics"]
author: "Dusan B. Jovanovic"
---

- What are the qualities of the design bellow?
- Can this be done simpler in C, wihtout losing the functionality?
- Can this be done using std::XYZ ?

```cpp
// https://wandbox.org/permlink/udzltQne483qGrat
// dbj@dbj.org from popular C++17 youtube examples
#include <iostream>
#include <variant>
#include <vector>
// vararg inheritance and overloading of thus inherited
// 'Functor' is a type that has public function call operator
// arguments are vararg of Functor types
template<typename ... Functors>
// inherit from var num of Functor types passed as 
// template arguments above
struct Ovld : Functors ... {
   // have here function call operators from all the Functors inherited
   // derive a call operator from all functors
   using Functors::operator() ... ;
};
// user defined deduction guide

template<typename...Functors> Ovld(Functors...) /*seeing this ctor */
->  /* induce */
Ovld<Functors...> ; /* this as being it's type */

// we do not have to use the above mechanism
// but we are not sure design principles 
// behind are not superior?
#define USE_OVERLORD
```
Funny enough we have this elaborate hierachy generator, but we do not like polymorphism. 

Instead we could have opted for this C++17 mechanisms bellow, to achieve (with no hacks) polymorphism with no inheritance. By using `std::variant`. And not using the `Ovld`.

```cpp        
// https://youtu.be/e2ZQyYr0Oi0
// shapes with no common ancestor
struct Circle {
void draw () { std::cout << "\n drawing Circle" ; }
};

struct Line {
void draw () {  std::cout << "\n drawing Line"   ; }
};

// basically std::variant is allowing us to 
// have one type for the std::vector
// used latter
using GeoObj = std::variant<Circle, Line> ;

// visit each GeoObj and call `draw()` on it
inline void drawer ( std::vector<GeoObj> shapes )
{
    for ( auto && geoobj : shapes )
    {
#if ! defined(USE_OVERLORD)   
// this stays unchanged if we add 'Triangle' 
    std::visit( [] ( auto && obj ) { obj.draw(); }, geoobj ) ;
#else       
    std::visit(
        // not created before here
    Ovld{
// give two functors as two lambdas to the ctor of Ovld
// caller needs to explicitly code for each shape here
    [] (Circle & c){ c.draw(); },
    [] (Line   & l){ l.draw(); }
    }, 
    geoobj );
#endif
    }
}

int main()
{
    std::vector<GeoObj> shapes{ Circle{}, Line{} };
    drawer( shapes );
    std::cout << "\n\nDONE!" << std::endl;
}
```        
`Ovld` is C++17, that also seems very complex to majority of C++ programmers. And certianly to **all** non C++ programmers.

But, it only generates a simple hierarchical structure ot Types given as `Ovld` template parameters. Each of them programers would probably understand this diagram immediately.

![plantuml](https://www.plantuml.com/plantuml/img/RO-z2W8n3CVtF4L6HGvkS2eE1peAFaDeAYtK7hJnYgZlRi_s5CGnl_z7aY49HRbUF80uyGPFasUqpaJIzePipYuOnkp4ujv5NHmK68-50YHDPTxsVT5PB01eJodLZZiWRgRHSSifnP7oQlt1SuTIXmgVIxOj-QPvCLHzJlrJuRrqz-XupA5hDJ-mNZsOmENX5m00)

Ovld working with `std::variant` dispatches the `draw` message based on the type. 

Instance of the `Ovld` is the visitor to the variant.

So, we have this advanced C++17 features, working together that generate this one simple type hierachy, and overloads functioning inside. Written in a very condensed code, that is hard to understand.

What are the prevailing benefits of the concepts on top of which `Ovld` is coded?

The key benefit is polymorphism with no inheritance.

- Is this resilient to change?
    - We avoid inheritance, true, but consider the changes necessary if you add `Triangle`.
- Is this functional but simple?
- Is this feasible to maintain?

As in the quantum phenomena: It depends on the oobserver.
