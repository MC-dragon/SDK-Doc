---
title: Float data type
---

Floats are approximations of real numbers written with decimals. If you don't need to work with decimals, use the Integer data type.

```crmscript
Integer i = 42;
Float f = 3.14;
```

## Numeric strings

Strings can have numeric content, but are always written in quotes.

### String toString(Integer decimals)

`toString()` is one of the most frequently used methods, typically when you are going to output something. It returns a string representation of an Float.

> [!NOTE]
> You must always specify how many decimal digits you want.

```crmscript!
Float pi = 3.14159;
for(Integer i = 0; i < 6; i++) {
  printLine(pi.toString(i));
}

```

## Math operators

| Operator | Description |
|:--------:|-------------|
| +        | add         |
| -        | subtract    |
| *        | multiply    |
| /        | divide      |
| %        | reminder    |
| ++       | increment   |
| --       | decrement   |

## Math functions

### Float abs()

`abs()`  will return the absolute value of a Float. That is, the non-negative value of the number without regarding the sign.

```crmscript!
Float i = -7.14;
print(i.abs().toString(2));
```

This example will print 7.14, without the sign.

### Integer floor()

`floor()` will return the Integer preceding the decimal separator. The floor of a Float is calculated by **rounding downward** to the nearest Integer.

```crmscript!
Float f = 13.456;
print(f.floor().toString());
```

This example will print 13.

### Integer round()

`round()` will return the Integer approximation of the Float without any decimals. It is calculated by **rounding to the nearest** Integer.

* if the 1st decimal is 5, 6, 7, 8, or 9 - round up
* if the 1st decimal is 0, 1, 2, 3, 4 - round down

```crmscript!
Float f = 13.79;
print(f.round().toString());
```

This example will print 14.

## Zero vs. no value

Before a Float is initialized, it has no value. This is commonly written as NULL, NUL, or NIL.

### Bool isNull()

`isNull()` will return **true** if it has no value and **false** if it does.