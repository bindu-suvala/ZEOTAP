# Errors Module

This module contains the exceptions raised by the package.

## Data

### `UNDEFINED`

A sentinel value indicating that something is undefined. When evaluated, this value is falsy.


---

## Exceptions

### `exception AttributeResolutionError`

**Bases**: `EvaluationError`

Raised when an attribute cannot be resolved to a value.

#### Constructor: `__init__(attribute_name, object_, thing=UNDEFINED, suggestion=None)`

#### Parameters:
- **`attribute_name`** (str): The name of the symbol that cannot be resolved.
- **`object_`**: The value that `attribute_name` was used as an attribute for.
- **`thing`**: The root object used to resolve `object_`.
- **`suggestion`** (str, optional): A suggestion for a valid attribute name.

---

### `exception AttributeTypeError`

**Bases**: `EvaluationError`

Raised when an attribute with type information resolves to a Python value that does not match the expected type.

#### Constructor: `__init__(attribute_name, object_type, is_value, is_type, expected_type)`

#### Parameters:
- **`attribute_name`** (str): The name of the symbol that cannot be resolved.
- **`object_type`**: The object on which `attribute_name` was resolved.
- **`is_value`**: The native Python value of the incompatible attribute.
- **`is_type`**: The rule-engine type of the incompatible attribute.
- **`expected_type`**: The expected rule-engine type for this attribute.

---

### `exception BytesSyntaxError`

**Bases**: `SyntaxError`

Raised for issues with improperly formatted bytes expressions.

#### Constructor: `__init__(message, value)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`value`** (str): The bytes value containing the syntax error.



---

### `exception DatetimeSyntaxError`

**Bases**: `SyntaxError`

Raised for issues with improperly formatted datetime expressions.

#### Constructor: `__init__(message, value)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`value`** (str): The datetime value containing the syntax error.

---

### `exception FloatSyntaxError`

**Bases**: `SyntaxError`

Raised for issues with improperly formatted float expressions.

#### Constructor: `__init__(message, value)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`value`** (str): The float value containing the syntax error.


---

### `exception EngineError`

**Bases**: `Exception`

The base exception class for other exceptions in this package.

#### Constructor: `__init__(message='')`

#### Parameters:
- **`message`** (str): Description of the error.

---

### `exception EvaluationError`

**Bases**: `EngineError`

Raised for issues occurring during the evaluation of a rule, which can happen at parse time while evaluating AST nodes.

---

### `exception FunctionCallError`

**Bases**: `EvaluationError`

Raised when there is an issue calling a function.

#### Constructor: `__init__(message, error=None, function_name=None)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`error`**: The original exception that triggered this error.
- **`function_name`** (str, optional): The name of the function that caused the error.



---

### `exception LookupError`

**Bases**: `EvaluationError`

Raised when a lookup operation fails to obtain an item from a container (analogous to `IndexError` and `KeyError`).

#### Constructor: `__init__(container, item)`

#### Parameters:
- **`container`**: The container object that the lookup was performed on.
- **`item`**: The key or index used for the lookup.



---

### `exception RegexSyntaxError`

**Bases**: `SyntaxError`

Raised for issues with improper regular expression syntax.

#### Constructor: `__init__(message, error, value)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`error`**: The `re.error` exception that triggered this error.
- **`value`** (str): The regular expression value containing the syntax error.

---

### `exception RuleSyntaxError`

**Bases**: `SyntaxError`

Raised for issues identified while parsing the grammar of the rule text.

#### Constructor: `__init__(message, token=None)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`token`**: The PLY token related to the syntax error (if available).

---

### `exception StringSyntaxError`

**Bases**: `SyntaxError`

Raised for issues with improperly formatted string expressions.

#### Constructor: `__init__(message, value)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`value`** (str): The string value containing the syntax error.



---

### `exception SymbolResolutionError`

**Bases**: `EvaluationError`

Raised when a symbol name cannot be resolved to a value.

#### Constructor: `__init__(symbol_name, symbol_scope=None, thing=UNDEFINED, suggestion=None)`

#### Parameters:
- **`symbol_name`** (str): The name of the symbol that cannot be resolved.
- **`symbol_scope`** (str, optional): The scope for symbol resolution.
- **`thing`**: The root object used to resolve the symbol.
- **`suggestion`** (str, optional): A suggestion for a valid symbol name.

*Changed in version 2.0.0: Added the `thing` parameter. Changed in version 3.2.0: Added the `suggestion` parameter.*

---

### `exception SymbolTypeError`

**Bases**: `EvaluationError`

Raised when a symbol with type information resolves to a Python value that is not of the expected type.

#### Constructor: `__init__(symbol_name, is_value, is_type, expected_type)`

#### Parameters:
- **`symbol_name`** (str): The name of the symbol that is of an incompatible type.
- **`is_value`**: The native Python value of the incompatible symbol.
- **`is_type`**: The rule-engine type of the incompatible symbol.
- **`expected_type`**: The expected rule-engine type for this symbol.

---

### `exception SyntaxError`

**Bases**: `EngineError`

A base error for syntax-related issues.

---

### `exception TimedeltaSyntaxError`

**Bases**: `SyntaxError`

Raised for issues with improperly formatted timedelta expressions.

#### Constructor: `__init__(message, value)`

#### Parameters:
- **`message`** (str): Description of the error.
- **`value`** (str): The timedelta value containing the syntax error.


---

## Exception Hierarchy

The class hierarchy for Rule Engine exceptions is:

EngineError 

    ├── EvaluationError 
    ├── AttributeResolutionError 
    ├── AttributeTypeError 
    ├── FunctionCallError 
    ├── LookupError  
    ├── SymbolResolutionError 
    └── SymbolTypeError
    └── SyntaxError 
    ├── BytesSyntaxError
    ├── DatetimeSyntaxError
    ├── FloatSyntaxError 
    ├── RegexSyntaxError 
    ├── RuleSyntaxError 
    ├── StringSyntaxError 
    └── TimedeltaSyntaxError
