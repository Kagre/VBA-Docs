---
title: CustomProperties Object (Word)
keywords: vbawd10.chm3553
f1_keywords:
- vbawd10.chm3553
ms.prod: word
api_name:
- Word.CustomProperties
ms.assetid: 8b4248a1-7e1f-dbbd-37ab-f52a2d1ee505
ms.date: 06/08/2017
---


# CustomProperties Object (Word)

A collection of  **[CustomProperty](Word.CustomProperty.md)** objects that represents the properties related to a smart tag. The **CustomProperties** collection includes all the smart tag custom properties in a document.


## Remarks

Use the  **[Properties](./overview/Word.md)** property to return a single **CustomProperties** object. Use the **[Add](Word.CustomProperties.Add.md)** method of the **CustomProperties** object with to create a custom property from within a Microsoft Word Visual Basic for Applications project. This example creates a new property for the first smart tag in the active document and displays the XML code used for the tag.


```vb
Sub AddProps() 
 With ActiveDocument.SmartTags(1) 
 .Properties.Add Name:="President", Value:=True 
<<<<<<< HEAD
 MsgBox "The XML code is " &; .XML 
=======
 MsgBox "The XML code is " & .XML 
>>>>>>> master
 End With 
End Sub
```

Use  **Properties** (Index) to return a single property for a smart tag, where Index is the number of the property. This example displays the name and value of the first property of the first smart tag in the current document.




```vb
Sub ReturnProps() 
 With ActiveDocument.SmartTags(1).Properties(1) 
<<<<<<< HEAD
 MsgBox "The Smart Tag name is: " &; .Name &; vbLf &; .Value 
=======
 MsgBox "The Smart Tag name is: " & .Name & vbLf & .Value 
>>>>>>> master
 End With 
End Sub
```

Use the  **[Count](Word.CustomProperties.Count.md)** property to return the number of custom properties for a smart tag. This example loops through all the smart tags in the current document and then lists in a new document the name and value of the custom properties for all smart tags that have custom properties.




```vb
Sub SmartTagsProps() 
 Dim docNew As Document 
 Dim stgTag As SmartTag 
 Dim stgProp As CustomProperty 
 Dim intTag As Integer 
 Dim intProp As Integer 
 
 Set docNew = Documents.Add 
 
 'Create heading info in new document 
 With docNew.Content 
<<<<<<< HEAD
 .InsertAfter "Name" &; vbTab &; "Value" 
=======
 .InsertAfter "Name" & vbTab & "Value" 
>>>>>>> master
 .InsertParagraphAfter 
 End With 
 
 'Loop through smart tags in current document 
 For intTag = 1 To ActiveDocument.SmartTags.Count 
 
 With ActiveDocument.SmartTags(intTag) 
 
 'Verify that the custom properties 
 'for smart tags is greater than zero 
 If .Properties.Count > 0 Then 
 
 'Loop through the custom properties 
 For intProp = 1 To .Properties.Count 
 
 'Add custom property name to new document 
 docNew.Content.InsertAfter .Properties(intProp) _ 
<<<<<<< HEAD
 .Name &; vbTab &; .Properties(intProp).Value 
=======
 .Name & vbTab & .Properties(intProp).Value 
>>>>>>> master
 docNew.Content.InsertParagraphAfter 
 Next 
 Else 
 
 'Display message if there are no custom properties 
<<<<<<< HEAD
 MsgBox "There are no custom properties for the " &; _ 
=======
 MsgBox "There are no custom properties for the " & _ 
>>>>>>> master
 "smart tags in your document." 
 End If 
 End With 
 Next 
 
 'Convert the content in the new document into a table 
 docNew.Content.Select 
 Selection.ConvertToTable Separator:=wdSeparateByTabs, NumColumns:=2 
 
End Sub
```


## See also


[Word Object Model Reference](./overview/Word/object-model.md)


