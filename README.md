# Engine Module

This module provides the primary external API for the package.

## Functions

### `resolve_attribute(thing, name)`

A replacement resolver function that looks up symbols as members of `thing`, similar to `thing.name`. The `thing` object can be a `namedtuple`, a custom Python class, or any object. All members of `thing` must be of a compatible data type.

**Warning:** This exposes all members of `thing`. For sensitive members, use a custom resolver that checks against a whitelist of allowed attributes.

#### Parameters:
- **`thing`**: The object from which the name attribute will be accessed.
- **`name`** (str): The symbol name being resolved.

#### Returns:
- The value corresponding to the specified attribute name.

---

### `resolve_item(thing, name)`

A resolver function for looking up symbols as items from an object (`thing`) that supports the Mapping interface (e.g., a dictionary). This is similar to `thing['name']`.

#### Parameters:
- **`thing`**: The object from which the name item will be accessed.
- **`name`** (str): The symbol name being resolved.

#### Returns:
- The value corresponding to the specified item name.

---

### `type_resolver_from_dict(dictionary)`

Returns a function suitable for use as the `type_resolver` for a Context instance from a dictionary. If any values in the dictionary are not of a compatible data type, a `TypeError` will be raised. The resulting function will raise a `SymbolResolutionError` if the symbol name does not exist within the dictionary.

#### Parameters:
- **`dictionary`** (dict): A dictionary (or any object supporting the Mapping interface) from which to create the callback function.

#### Returns:
- The callback function.

---

## Classes

### `class Context`

Defines the context for a rule’s evaluation, allowing modifications to symbol resolution and regex flag usage.

#### Constructor: `__init__(*, regex_flags=0, resolver=None, type_resolver=None, default_timezone='local', default_value=UNDEFINED, decimal_context=None)`

#### Parameters:
- **`regex_flags`** (int): Flags for the `re` module when calling `match()` or `search()` for comparison expressions.
- **`resolver`**: Optional callback function to use in place of `resolve()`.
- **`type_resolver`** (function or dict): Optional callback function to use in place of `resolve_type()`.
- **`default_timezone`** (str or tzinfo): Default timezone for datetime instances without a specified timezone. Accepts `tzinfo` instances or the strings "local" or "utc".
- **`default_value`**: Default value when resolving missing symbols or attributes.
- **`decimal_context`**: Specific `decimal.Context` object for evaluating FLOAT values. Defaults to the current thread’s context.

**Notes:**
- *Changed in version 2.0.0: Added the `default_value` parameter.*
- *Changed in version 2.1.0: If `type_resolver` is a dictionary, `type_resolver_from_dict()` is called automatically.*
- *Changed in version 3.0.0: Added the `decimal_context` parameter.*

#### Methods:
- **`assignments(*assignments)`**: Adds specified assignments to a thread-specific scope.

---

### `class Rule`

Parses a string with a logical expression and evaluates an arbitrary object for matching based on that expression.

#### Constructor: `__init__(text, context=None)`

#### Parameters:
- **`text`** (str): The text of the logical expression.
- **`context`** (Context): The context for evaluating the expression. Default is `Context`.

#### Methods:
- **`evaluate(thing)`**: Evaluate the rule against the specified object.
- **`filter(things)`**: Iterate over `things` and yield each member that matches.
- **`is_valid(text, context=None)`**: Check if the rule is syntactically correct.
- **`matches(thing)`**: Evaluate the rule against the specified object to determine if it matches.

#### Attributes:
- **`parser`**: The Parser instance used for parsing the rule text into an abstract syntax tree (AST).
- **`to_graphviz()`**: Generate a diagram of the parsed rule’s AST using GraphViz.

---

