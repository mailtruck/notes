
property_exists

(PHP 5 >= 5.1.0, PHP 7)
property_exists — Checks if the object or class has a property

Description

```
bool property_exists ( mixed $class , string $property )
```

This function checks if the given property exists in the specified class.

Note:
As opposed with isset(), property_exists() returns TRUE even if the property has the value NULL.

