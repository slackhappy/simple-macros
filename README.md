# simple-macros #
A collection of simple Scala [macros](http://docs.scala-lang.org/overviews/macros/overview.html)

## Adding simple macros to your build ##
The project is compiled for Scala 2.10.4. In your build.sbt, add:

    "com.foursquare" %% "simple-macros" % "0.5"


## How to build ##
    ./sbt compile
    ./sbt test

## How to use ##
[API Documentation](http://foursquare.github.io/simple-macros/api)

## CodeRef Example ##
```scala
import com.foursquare.macros.CodeRef
import com.foursquare.macros.CodeRef._

// Explicit call. here now contains the
// current file (path relative to compiler wd)
// and line number
val here: CodeRef = CODEREF

// Implicit reference to caller.  Gives you the
// line from which the method was called without
// taking a stack trace.
def foo(bar: Int)(implicit caller: CodeRef) {
  println("called foo(" + bar + ") at " + caller)
}
foo(1)
```

## Frame Example ##

```scala
import com.foursquare.macros.Frame._

// Explicit call. here now contains the
// standard StackTraceElement
val here: StackTraceElement = FRAME

// Implicit reference to caller.  Gives you the
// StackTraceElement from which the method was called without
// taking a stack trace.
def foo(bar: Int)(implicit caller: StackTraceElement) {
  println("called foo(" + bar + ") at " + caller)
}
foo(2)
```

## Contributors ##
- Jeff Jenkins
- John Gallagher
