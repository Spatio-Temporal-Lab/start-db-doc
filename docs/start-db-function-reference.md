# DataTypeConversionFunction
| Function                   | Describe                                                                                              | Example                                               | 
|:---------------------------|:------------------------------------------------------------------------------------------------------|:------------------------------------------------------|
| castToInteger (str:String) | Receive a string parameter, convert the string type to integer type, and return an integer type value | `select castToInteger ("1234")` <br/> -- return 1234  |
| castToLong (str:String)    | Receive a string parameter, convert the string type to Long type, and return a Long type value        | `select castToLong ("1234")`<br/> -- return 1234L     |
| castToFloat (str:String)   | Receive a string parameter, convert the string type to Float type, and return a Float type value      | `select castToFloat ("123.1")` <br/> -- return 123.1f |
| castToDouble (str:String)  | Receive a string parameter, convert the string type to Double type, and return a Double type value    | `select castToDouble ("123.1")`<br/> -- return 123.1d |
| castToBoolean (str:String) | Receive a string parameter, convert the string type to Boolean type, and return a Boolean type value  | `select castToBoolean ("true")`<br/> -- return true   |
| castToString (any:Object)  | Receive a Object parameter, convert the Object type to String type, and return a String type value    | `selec castToString (1234)`<br/> -- return "1234"     |
| parseInteger (num:Object)  | Receive a Object parameter, convert the Object type to Integer type, and return a Integer type value  | `select parseInteger (1234)` <br/> -- return 1234     |
| parseLong (num:Object)     | Receive a Object parameter, convert the Object type to Long type, and return a Long type value        | `select parseLong (1234)`<br/> -- return 1234l        |
| parseDouble (num:Object)   | Receive a Object parameter, convert the Object type to Double type, and return a Double type value    | `select parseDouble (1234)` <br/> -- return 1234d     |




 
 
 





  

