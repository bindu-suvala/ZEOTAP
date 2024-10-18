# Suggestions Module


This module contains helper functions designed to provide suggestions when errors occur.

## Functions

### `suggest_symbol(word, options)`

Selects the best match for the given `word` from a list of value options. Symbols that are not suitable names will be filtered out. If no suitable match is found, the function will return `None`.

#### Parameters:
- **`word`** (str): The original word for which an alternative suggestion is sought.
- **`options`** (tuple): A list of strings from which to select the best match.

#### Returns:
- The best replacement for the `word`, or `None` if no suitable match is found.

#### Return type:
- `str` or `None`

---


