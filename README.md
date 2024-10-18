# Types Module


This module contains internal type definitions and utility functions for working with them.

## Functions

### `coerce_value(value, verify_type=True)`

Converts a native Python value to a data type that can be represented by a Rule Engine DataType. This function is particularly useful for converting values at the engine boundaries, such as when resolving symbols from external objects.

#### Parameters:
- **`value`**: The value to convert.
- **`verify_type`** (bool): Indicates whether to verify the converted value’s type.

#### Returns:
- The converted value.

---

### `is_integer_number(value)`

Checks whether the given value is an integer number (i.e., a whole number). This can be used to determine if a floating-point number like `3.0` can be safely converted to an integer without loss of information.

#### Parameters:
- **`value`**: The value to check (native Python type).

#### Returns:
- `True` if the value is an integer number; otherwise, `False`.

#### Return type:
- `bool`

---

### `is_natural_number(value)`

Checks whether the given value is a natural number (i.e., a whole, non-negative number).

#### Parameters:
- **`value`**: The value to check (native Python type).

#### Returns:
- `True` if the value is a natural number; otherwise, `False`.

#### Return type:
- `bool`

---

### `is_numeric(value)`

Checks whether the given value is numeric (i.e., capable of being represented as a floating-point value without loss of information).

#### Parameters:
- **`value`**: The value to check (native Python type).

#### Returns:
- `True` if the value is numeric; otherwise, `False`.

#### Return type:
- `bool`

---

### `is_real_number(value)`

Checks whether the given value is a real number (i.e., can be represented as a finite floating-point value). Note that NaN is not considered a real number.

#### Parameters:
- **`value`**: The value to check (native Python type).

#### Returns:
- `True` if the value is a real number; otherwise, `False`.

#### Return type:
- `bool`

---

### `iterable_member_value_type(python_value)`

Returns the corresponding data type of each member of a native `python_value` if the types are either the same or NULL. This allows for nullable values in iterables.

#### Returns:
- The data type of the sequence members. This will never be NULL; it will either be `UNSPECIFIED` or another type.

---

## Classes

### `class DataType`

A collection of constants representing different supported data types. There are three ways to compare data types:

- **Equality checking**: `dt == DataType.TYPE`
- **Class checking**: `isinstance(dt, DataType.TYPE.__class__)`
- **Compatibility checking**: `DataType.is_compatible(dt, DataType.TYPE)`

#### Static Methods

- **`ARRAY(value_type, value_type_nullable=True)`**: Defines an array type.
- **`FUNCTION(name, return_type=UNDEFINED, argument_types=UNDEFINED, minimum_arguments=None)`**: Defines a function type.
- **`MAPPING(key_type, value_type=UNDEFINED, value_type_nullable=True)`**: Defines a mapping type.
- **`SET(value_type, value_type_nullable=True)`**: Defines a set type.
- **`UNDEFINED`**: Represents undefined values.

#### Class Methods

- **`from_name(name)`**: Get the data type from its name.
- **`from_type(python_type)`**: Get the supported data type constant for the specified Python type or type hint.
- **`from_value(python_value)`**: Get the supported data type constant for the specified Python value.
- **`is_compatible(dt1, dt2)`**: Check if two data type definitions are compatible without conversion.
- **`is_definition(value)`**: Check if a value is a data type definition.

---

