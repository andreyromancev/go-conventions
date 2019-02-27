# Go conventions

## Modules
### Module name should be short
But should not take good variable names.
### Module name should be singular

## Variables
### Variable names should be in camelCase
Including function arguments.

## Structure
### Mutex hat
Mutex should be declared above variables it protects.
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
