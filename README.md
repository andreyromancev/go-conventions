# Go conventions

## Modules
### Module name should be short
But should not take good variable names.

## Structure
# Use mutex head
Mutex should be difined above variables it protects.
```
struct {
	...

	// rateMu protects rateLimits and mostRecent.
	rateMu     sync.Mutex
	rateLimits [categories]Rate
	mostRecent rateLimitCategory
}
```
