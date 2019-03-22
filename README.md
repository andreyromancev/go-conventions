# Go conventions

## Naming
* Module name should be short, but should not take good variable names.
* Module name should be a single word
* Module name should not be generic ("base", "common", "util", etc.)
* Type names should not contain its category (i.e. interface, implementation etc.).
* Variable name should be in camelCase, including function arguments.
* Variable name should not contain its type.
* The greater the distance between a name’s declaration and its last use, the longer the name should be.
* Variable name should be short and concise.
* Getter name should not contain `get` prefix.

## Functions and methods
* Functions should return concrete types, but expect interfaces.

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
* Function `init` should be declared before other types (in the beginning of file).

## Errors
* Error text should not start from a capital letter or end with a `.`.

## Comments
* Comment shoud be a complete sentence and end with a `.`.

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
