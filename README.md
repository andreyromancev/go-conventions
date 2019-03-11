# Go conventions

## Naming
* Module name should be short, but should not take good variable names.
* Variable name should be in camelCase, including function arguments.
* Variable name should not contain its type
* Type names should not contain its category (i.e interface, implementation etc.)
* Variable name should be short and concise
* Getter name should not contain `get` prefix

## Functions and methods
* Return concrete types, expect interfaces

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
