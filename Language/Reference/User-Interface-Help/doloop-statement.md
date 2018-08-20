---
title: Do...Loop Statement
keywords: vblr6.chm1008790
f1_keywords:
- vblr6.chm1008790
ms.prod: office
ms.assetid: f1ac3901-238d-3e38-45dc-f659fd88c23b
ms.date: 06/08/2017
---


# Do...Loop Statement

Repeats a block of [statements](../../Glossary/vbe-glossary.md) while a condition is **True** or until a condition becomes **True**.

 **Syntax**

 **Do** [{ **While** |**Until** } _condition_ ]
[ _statements_ ]
[ **Exit Do** ]
[ _statements_ ]

 **Loop**
Or, you can use this syntax:
 **Do**
[ _statements_ ]
[ **Exit Do** ]
[ _statements_ ]
 **Loop** [{ **While** |**Until** } _condition_ ]
The  **Do Loop** statement syntax has these parts:


|**Part**|**Description**|
|:-----|:-----|
| _condition_|Optional. [Numeric expression](../../Glossary/vbe-glossary.md) or[string expression](../../Glossary/vbe-glossary.md) that is **True** or **False**. If _condition_ is[Null](../../Glossary/vbe-glossary.md),  _condition_ is treated as **False**.|
| _statements_|One or more statements that are repeated while, or until,  _condition_ is **True**.|

 **Remarks**
Any number of  **Exit Do** statements may be placed anywhere in the **Do…Loop** as an alternate way to exit a **Do…Loop**. **Exit Do** is often used after evaluating some condition, for example, **If…Then**, in which case the **Exit Do** statement transfers control to the statement immediately following the **Loop**.
When used within nested  **Do…Loop** statements, **Exit Do** transfers control to the loop that is one nested level above the loop where **Exit Do** occurs.

## Example

This example shows how  **Do...Loop** statements can be used. The inner **Do...Loop** statement loops 10 times, asks the user if it should keep going, sets the value of the flag to **False** when they select **No**, and exits prematurely using the **Exit Do** statement. The outer loop exits immediately upon checking the value of the flag.


```vb
Public Sub LoopExample()
    Dim Check As Boolean, Counter As Long, Total As Long
    Check = True: Counter = 0: Total = 0 ' Initalize variables.
    Do ' Outer loop.
        Do While Counter < 20 ' Inner Loop
            Counter = Counter + 1 ' Increment Counter.
            If Counter Mod 10 = 0 Then ' Check in with the user on every multiple of 10.
                Check = (MsgBox("Keep going?", vbYesNo) = vbYes) ' Stop when user click's on No
                If Not Check Then Exit Do ' Exit inner loop.
            End If
        Loop
        Total = Total + Counter ' Exit Do Lands here.
        Counter = 0
    Loop Until Check = False ' Exit outer loop immediately.
    MsgBox "Counted to: " & Total
End Sub
```
