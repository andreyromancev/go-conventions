# Go conventions

## Naming
* Naming is important. Always.
* Module name should be short, but should not take good variable names.
* Module name should be a single word
* Module name should not be generic ("base", "common", "util", etc.)
* Type names should not contain its category (i.e. interface, implementation etc.).
* Variable and constant names should be in camelCase, including function arguments.
* Variable and constant names should not contain its type.
* The greater the distance between a name’s declaration and its last use, the longer the name should be.
* Variable name should be short and concise.
* Getter name should not contain `get` prefix.
* Words in names that are initialisms or acronyms (e.g. "URL" or "NATO") have a consistent case. For example, "URL" should appear as "URL" or "url" (as in "urlPony", or "URLPony"), never as "Url". 

## Functions and methods
* Functions should return concrete types, but expect interfaces.
* Functions and methods should not use named return parameters. Function size doesn't matter.
* Happy path inside a function should have the smallest indent. I.e. Use early return on negative paths (like return error). 
* Package-level function `init` should be discouraged.

## Interfaces
* Interface should describe behaviour, not object.

## Declarations
* Mutex should be declared above variables it protects.
	```
	struct {
		...

		// rateMu protects rateLimits and mostRecent.
		rateMu     sync.Mutex
		rateLimits [categories]Rate
		mostRecent rateLimitCategory

		// New variable declaration is separated by an empty line.
		common service
	}
	```

## Errors
* Error text should not start from a capital letter or end with a `.`.
* Returning error should be discouraged if it's possible to handle it in the returning funciton.
* Errors should be handled only once. For example, a code like this should be discouraged:
	```
	func WriteAll(w io.Writer, buf []byte) error {
		_, err := w.Write(buf)
		if err != nil {
			log.Println("unable to write:", err) // annotated error goes to log file
			return err                           // unannotated error returned to caller
		}
		return nil
	}
	```

## Comments
* Comment shoud be a complete sentence and end with a `.`.
* Comments on variables and constants should describe their contents, not their purpose.
* Comments on functions should describe how to use them and (optionally) what they do.

## API
* API should be designed for its default use case.
* `nil` as a parameter should be discouraged.

## Concurrency
* Concurrency should be left to the caller. I.e. code should be synchronous be default.
* Code that starts a Goroutine is responsible for its lifetime.


## Context
* Context should be passed as the first parameter in the function. Never inside another struct.

## Testing
* Unit tests should be in the same package.
* Unit tests should be black box (except when a certain test case cannot be achieved via black box).
* Unit tests should use fuzzing in addition to hard-coded values, when possible.

## External tooling
* `go:generate` commands should be declared one line before godoc for type.
	```
	// go:generate stringer -type=MyAwesomeType
        
	// MyAwesomeType can do anything and everything!
	type MyAwesomeType struct {}
	```
