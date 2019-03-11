# Go conventions

## Naming
* Module name should be short, but should not take good variable names.
* Module name should be a single word
* Module name should bot be generic ("base", "common", "util", etc.)
* Type names should not contain its category (i.e interface, implementation etc.).
* Variable name should be in camelCase, including function arguments.
* Variable name should not contain its type.
* The greater the distance between a name’s declaration and its uses, the longer the name should be.
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


# TODO
### Should one export struct that returned from constructor.
