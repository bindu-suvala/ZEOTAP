# Parser Module

This module contains the parsing logic for converting rule text written in a specified grammar into an abstract syntax tree (AST) that can be evaluated later.

## Utilities

### Classes

#### `class Parser`

**Bases**: `ParserBase`

The parser class for the rule grammar. This class includes numerous PLY-specific members to define various components of the grammar, enabling it to be parsed and reduced into an AST. Once constructed, the AST can be evaluated multiple times. To enhance efficiency, nodes within the AST that can be reduced are evaluated during the parsing process, which may lead to `EvaluationError` exceptions being raised.

##### Constructor: `__init__(debug=False)`

##### Parameters:
- **`debug`** (bool): Whether to enable debugging features when using the PLY API.

---

#### `class ParserBase`

**Bases**: `object`

A base class for parser objects to inherit from. This class does not include any grammar-related definitions.

##### Constructor: `__init__(debug=False)`

##### Parameters:
- **`debug`** (bool): Whether to enable debugging features when using the PLY API.

---

##### Method: `parse(text, context, **kwargs)`

Parses the specified text into an AST of nodes that can later be evaluated. This occurs in two phases: first, the syntax is parsed to construct a tree of deferred/uninitialized AST nodes. Next, each node is built recursively using its respective `rule_engine.ast.ASTNodeBase.build()` method.

###### Parameters:
- **`text`** (str): The grammar text to parse into an AST.
- **`context`** (`Context`): The context for specifying parsing and evaluation options.

###### Returns:
- The parsed AST statement.

###### Return type:
- `Statement`

---

### Attributes

- **`precedence`**: A tuple defining the precedence of operators.
- **`reserved_words`**: A mapping of literal words reserved for grammar to their corresponding grammar names.

---

