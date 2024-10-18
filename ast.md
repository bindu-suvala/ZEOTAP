# AST

This module contains the nodes that comprise the abstract syntax tree generated from parsed grammar text.

## Classes
### class Assignment(name, *, value=UNDEFINED, value_type=None)[source]
Bases: object

An internal assignment whereby a symbol is populated with a value of the specified type.

#### __init__(name, *, value=UNDEFINED, value_type=None)[source]
#### Parameters:
- `name (str)` – The symbol name that the assignment is defining.
- `value` – The value of the assignment.
- `value_type (DataType)` – The data type of the assignment.

#### Attributes:
- `name`
- `value`
- `value_type`
### class Statement
Bases: ASTNodeBase

A class representing the top-level statement of the grammar text.
### class ExpressionBase[source]
Bases: ASTNodeBase

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class LeftOperatorRightExpressionBase
Bases: ExpressionBase

A base class for representing complex expressions composed of a left side and a right side, separated by an operator.

#### Parameters:
- `context (Context)` – The context to use for evaluating the expression.
- `type (str)` – The grammar type of operator at the center of the expression. Subclasses must define operator methods to handle evaluation based on this value.
- `left (ExpressionBase)` – The expression to the left of the operator.
- `right (ExpressionBase)` – The expression to the right of the operator.

#### Attributes:
- `compatible_types` – A tuple containing the compatible data types that the left and right expressions must return.
### class LiteralExpressionBase(context, value)[source]
Bases: ExpressionBase

A base class for representing literal values from the grammar text.

#### Parameters:
- `context (Context)` – The context to use for evaluating the expression.
- `value` – The native Python value.
### class AddExpression
Bases: LeftOperatorRightExpressionBase

A class for representing addition expressions from the grammar text.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class SubtractExpression
Bases: LeftOperatorRightExpressionBase

A class for representing subtraction expressions from the grammar text.

*Added in version 3.5.0.*

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class ArithmeticExpression
Bases: LeftOperatorRightExpressionBase

A class for representing arithmetic expressions from the grammar text such as multiplication and division.

#### Attributes:
- `result_type= FLOAT`
  - The data type of the result of successful evaluation.
### class ArithmeticComparisonExpression
Bases: ComparisonExpression

A class for representing arithmetic comparison expressions from the grammar text such as less-than-or-equal-to and greater-than.

#### Attributes:
- `result_type= BOOLEAN`
  - The data type of the result of successful evaluation.
### class BitwiseExpression
Bases: LeftOperatorRightExpressionBase

A class for representing bitwise arithmetic expressions from the grammar text such as XOR and shifting operations.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class ComparisonExpression
Bases: LeftOperatorRightExpressionBase

A class for representing comparison expressions from the grammar text such as equality checks.

#### Attributes:
- `result_type= BOOLEAN`
  - The data type of the result of successful evaluation.
### class LogicExpression
Bases: LeftOperatorRightExpressionBase

A class for representing logical expressions from the grammar text such as “and” and “or”.

#### Attributes:
- `result_type= BOOLEAN`
  - The data type of the result of successful evaluation.
### class ArrayExpression
Bases: _CollectionMixin, LiteralExpressionBase

Literal array expressions containing 0 or more sub-expressions.

#### Attributes:
- `result_type= ARRAY`
  - The data type of the result of successful evaluation.
### class BooleanExpression
Bases: LiteralExpressionBase

Literal boolean expressions representing True or False.

#### Attributes:
- `result_type= BOOLEAN`
  - The data type of the result of successful evaluation.
### class BytesExpression
Bases: LiteralExpressionBase

Literal bytes expressions representing a binary string. This expression type always evaluates to true when not empty.

#### Attributes:
- `result_type= BYTES`
  - The data type of the result of successful evaluation.
### class DatetimeExpression
Bases: LiteralExpressionBase

Literal datetime expressions representing a specific point in time. This expression type always evaluates to true.

#### Attributes:
- `result_type= DATETIME`
  - The data type of the result of successful evaluation.
### class FloatExpression
Bases: LiteralExpressionBase

Literal float expressions representing numerical values.

#### Attributes:
- `result_type= FLOAT`
  - The data type of the result of successful evaluation.
### class FunctionExpression
Bases: LiteralExpressionBase

Literal mapping expression representing a function.

#### Attributes:
- `result_type= FUNCTION`
  - The data type of the result of successful evaluation.
### class MappingExpression
Bases: LiteralExpressionBase

Literal mapping expression representing a set of associations between keys and values.

#### Attributes:
- `result_type= MAPPING`
  - The data type of the result of successful evaluation.
### class NullExpression
Bases: LiteralExpressionBase

Literal null expressions representing null values. This expression type always evaluates to false.

#### Attributes:
- `result_type= NULL`
  - The data type of the result of successful evaluation.
### class SetExpression
Bases: _CollectionMixin, LiteralExpressionBase

Literal set expressions containing 0 or more sub-expressions.

#### Attributes:
- `result_type= SET`
  - The data type of the result of successful evaluation.
### class StringExpression
Bases: LiteralExpressionBase

Literal string expressions representing an array of characters.

#### Attributes:
- `result_type= STRING`
  - The data type of the result of successful evaluation.
### class StringExpression
Bases: LiteralExpressionBase

Literal string expressions representing an array of characters.

#### Attributes:
- `result_type= STRING`
  - The data type of the result of successful evaluation.
### class TimedeltaExpression
Bases: LiteralExpressionBase

Literal timedelta expressions representing an offset from a specific point in time.



#### Attributes:
- `result_type= TIMEDELTA`
  - The data type of the result of successful evaluation.
### class ComprehensionExpression(context, result, variable, iterable, condition=None)[source]
Bases: ExpressionBase

#### Attributes:
- `result_type= ARRAY`
  - The data type of the result of successful evaluation.
### class ContainsExpression
Bases: ExpressionBase

An expression used to test whether an item exists within a container.

#### Attributes:
- `result_type= BOOLEAN`
  - The data type of the result of successful evaluation.
### class GetAttributeExpression(context, object_, name, safe=False)[source]
Bases: ExpressionBase

A class representing an expression in which name is retrieved as an attribute of object.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class GetItemExpression(context, container, item, safe=False)[source]
Bases: ExpressionBase

A class representing an expression in which an item is retrieved from a container object.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class GetSliceExpression(context, container, start=None, stop=None, safe=False)[source]
Bases: ExpressionBase

A class representing an expression in which a range of items is retrieved from a container object.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class SymbolExpression
Bases: ExpressionBase

A class representing a symbol name to be resolved at evaluation time with the help of a Context object.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class TernaryExpression
Bases: ExpressionBase

A class for representing ternary expressions from the grammar text. These involve evaluating condition before evaluating either case_true or case_false based on the results.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
### class UnaryExpression
Bases: ExpressionBase

A class for representing unary expressions from the grammar text. These involve a single operator on the left side.

#### Attributes:
- `result_type= UNDEFINED`
  - The data type of the result of successful evaluation.
