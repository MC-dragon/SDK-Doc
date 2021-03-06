---
title: Void setGenericFromString(Generic generic, String value)
path: /EJScript/Classes/Generic/Member functions/Void setGenericFromString(Generic generic, String value)
intellisense: 1
langref: 1
sortOrder: 170
keywords: setGenericFromString(Generic,String)
---


Sets the value of a variable (any variable will automatically be up-casted to a Generic) from a string.


This function will only work for variables of basic types (String, Integer, Float, etc). For arrays or any other types it will throw an exception. In combination with e.g. `getStructMembers()` and `getGenericValue()`, this function can be used to iterate a struct and set all its members programmatically instead of having to explicit hard-code each one of them.


* **generic:** Generic Variable to set the value of
* **value:** String Value to set. Value must be formatted according to what the type understands, specifically date/time/datetime needs to be YYYY-MM-DD HH:MI:SS (first or last part for date/time).
