
# ast

This module contains the nodes which comprise the abstract syntax tree generated from parsed grammar text.




## classes



```bash
  
 class Assignment(name, *, value=UNDEFINED, value_type=None):
    """An internal assignment whereby a symbol is populated with a value of the specified type."""
    __bases__ = (object,)

    def __init__(self, name, *, value=UNDEFINED, value_type=None):
        """
        Parameters:
            name (str): The symbol name that the assignment is defining.
            value: The value of the assignment.
            value_type (DataType): The data type of the assignment.
        """
        self.name = name
        self.value = value
        self.value_type = value_type


```
# statement

```bash
  
 class Statement(context, expression, comment=None):
    """Represents the top-level statement of the grammar text."""
    __bases__ = (ASTNodeBase,)


```
# ExpressionBase

```bash
  class ExpressionBase:
    """Base class for all expressions."""
    __bases__ = (ASTNodeBase,)
    result_type = UNDEFINED

```
# LeftOperatorRightExpressionBase
```bash
 
class LeftOperatorRightExpressionBase(context, type_, left, right):
    """Base class for complex expressions with left and right operands."""
    __bases__ = (ExpressionBase,)

    def __init__(self, context, type_, left, right):
        """
        Parameters:
            context (Context): The context to use for evaluating the expression.
            type (str): The grammar type of the operator.
            left (ExpressionBase): The left expression.
            right (ExpressionBase): The right expression.
        """
        self.context = context
        self.type = type_
        self.left = left
        self.right = right

```
# Additional Classes

AddExpression

```bash
  class AddExpression(*args, **kwargs):
    """Class for representing addition expressions from the grammar text."""
    __bases__ = (LeftOperatorRightExpressionBase,)
    result_type = UNDEFINED

```
SubtractExpression

```bash
class SubtractExpression(*args, **kwargs):
    """Class for representing subtraction expressions from the grammar text."""
    __bases__ = (LeftOperatorRightExpressionBase,)
    result_type = UNDEFINED

```
ArithmeticExpression

```bash
class ArithmeticExpression(context, type_, left, right):
    """Class for representing arithmetic expressions."""
    __bases__ = (LeftOperatorRightExpressionBase,)
    result_type = FLOAT

```
ComparisonExpression

```bash
class ComparisonExpression(context, type_, left, right):
    """Class for representing comparison expressions."""
    __bases__ = (LeftOperatorRightExpressionBase,)
    result_type = BOOLEAN

```

