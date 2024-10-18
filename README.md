# Builtins Module

This module defines the built-in values for the engine, providing a context for rules.

## Class: `Builtins`

### Overview
The `Builtins` class allows you to define and access variables within the built-in context of rules. Access these variables by prefixing the symbol name with a `$`.

### Constructor: `__init__(values, namespace=None, timezone=None, value_types=None)`

#### Parameters:
- **`values`** (dict): 
  - A mapping of string keys representing symbol names.
  - Values can be either Python literals or functions. If a function is used, it will be called with the instance of `Builtins` as an argument.
  
- **`namespace`** (str, optional): 
  - The namespace for resolving the variables.
  
- **`timezone`** (tzinfo, optional): 
  - A timezone to use when resolving timestamps.
  
- **`value_types`** (dict, optional): 
  - A mapping of values to their corresponding data types.

**Note:** 
*Changed in version 2.3.0: Added the `value_types` parameter.*

### Class Method: `from_defaults(values=None, **kwargs)`

Initializes a `Builtins` instance with a predefined set of default values.

### Method: `resolve_type(name)`

Determines the data type of a built-in symbol.

#### Parameters:
- **`name`** (str): 
  - The name of the symbol for which to retrieve the data type.

#### Returns:
- The data type of the symbol, or `UNDEFINED`.

### Constant: `scope_name`

- **Value:** `'built-in'`  
  - Represents the identity name of the scope for built-in symbols.
