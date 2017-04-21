---
title: "Проверка по XML-схеме (XSD) с помощью XmlSchemaSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Проверка по XML-схеме (XSD) с помощью XmlSchemaSet
XML\-документы можно проверять на соответствие схеме XML в классе <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## Проверка XML\-документов  
 Проверка XML\-документов выполняется с помощью метода <xref:System.Xml.XmlReader.Create%2A> класса <xref:System.Xml.XmlReader>.  Чтобы выполнить проверку XML\-документа, создайте объект <xref:System.Xml.XmlReaderSettings>, содержащий схему XML, с помощью которой выполняется проверка XML\-документа.  
  
> [!NOTE]
>  Пространство имен <xref:System.Xml.Schema> содержит методы расширений, которые упрощают проверку XML\-дерева по сравнению с использованием XSD\-файла и [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  Дополнительные сведения о проверке XML\-документов с помощью LINQ to XML см. в разделе [Как выполнить проверку с помощью XSD](../Topic/How%20to:%20Validate%20Using%20XSD%20\(LINQ%20to%20XML\).md).  
  
 Отдельную схему или набор схем \(например, класс <xref:System.Xml.Schema.XmlSchemaSet>\) можно добавить в класс <xref:System.Xml.Schema.XmlSchemaSet>, передав ее в качестве параметра метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.  Обратите внимание, что при проверке документа целевое пространство имен документа должно соответствовать целевому пространству имен схемы в наборе схем.  
  
 Далее приведен пример XML\-документа.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Далее приведена схема, по которой проверяется XML\-документ из примера.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 В последующем примере кода схема добавляется к свойству <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> объекта <xref:System.Xml.XmlReaderSettings>.  Объект <xref:System.Xml.XmlReaderSettings> передается в качестве параметра в метод <xref:System.Xml.XmlReader.Create%2A> объекта <xref:System.Xml.XmlReader>, который проверяет XML\-документ.  
  
 Свойство <xref:System.Xml.XmlReaderSettings.ValidationType%2A> объекта <xref:System.Xml.XmlReaderSettings> устанавливается в `Schema`, чтобы включить проверку XML\-документа в методе <xref:System.Xml.XmlReader.Create%2A> объекта <xref:System.Xml.XmlReader>.  Обработчик <xref:System.Xml.Schema.ValidationEventHandler> добавляется в объект <xref:System.Xml.XmlReaderSettings>, чтобы обрабатывать все события <xref:System.Xml.Schema.XmlSeverityType> или <xref:System.Xml.Schema.XmlSeverityType>, вызванные в результате ошибок, найденных при проверке XML\-документа и схемы.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## См. также  
 [XmlSchemaSet для компиляции схемы](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)   
 [Работа с XML\-схемами](../../../../docs/standard/data/xml/working-with-xml-schemas.md)