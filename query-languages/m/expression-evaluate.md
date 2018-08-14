---
title: "Expression.Evaluate | Microsoft Docs"
ms.date: 4/16/2018
ms.prod: power-query
ms.reviewer: owend
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
---
# Expression.Evaluate

  
## About  
Evaluates a Text expression and returns the evaluated value.  
  
```  
Expression.Evaluate(expression as text, optional environment as [...]) as any  
```  
  
## Arguments  
  
|Argument|Description|  
|------------|---------------|  
|expression|The expression to evaluate.|  
|optional environment|The expression environment.|  
  
## Examples  
Expression.Evaluate("1 + 1") equals 2  
  
Expression.Evaluate("1 +") equals Error  
  
Expression.Evaluate(  
  
"section Section1; shared X = 1;"  
  
)  equals  Error, only expressions are supported  
  
Expression.Evaluate(  
  
"Record.Field([A=1], ""A"")"  
  
)  equals  error. Unknown identifier "Record.Field".  
  
Expression.Evaluate(  
  
"Record.Field([A=1], ""A"")",  
  
[Record.Field = Record.Field]  
  
)  equals  1  
  
let  
  
x = 1  
  
in  
  
Expression.Evaluate("x") equals Error. Unknown identifier "x".  
  
let  
  
x = 1  
  
in  
  
Expression.Evaluate(  
  
"x",  
  
\#shared  
  
) equals Error. Unknown identifier "x".  
  
let  
  
x = 1  
  
in  
  
Expression.Evaluate("x", [x = x]) equals 1  
  
section;  
  
shared MyText = "ABC";  
  
MyResult = Expression.Evaluate(  
  
"Text.StartsWith(MyText, ""A"")",  
  
\#shared  
  
); // true  
  
section;  
  
MyText = "ABC";  
  
MyResult = Expression.Evaluate(  
  
"Text.StartsWith(MyText, ""A"")",  
  
\#shared  
  
); equals Error. Unknown identifier "MyText" (since MyText isn't shared).  
  