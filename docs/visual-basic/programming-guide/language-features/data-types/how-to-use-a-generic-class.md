---
title: Практическое руководство. Использование универсального класса (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 108532e5b765fa918fa894199ef710a9f52db4e4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658578"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Практическое руководство. Использование универсального класса (Visual Basic)
Класс, принимающий *параметры типа*, называется *универсальным*. При использовании универсального класса из него можно создать *сконструированный класс*, указав *аргумент типа* для каждого из этих параметров. После этого можно объявить переменную типа сконструированного класса, а также создать экземпляр такого класса и присвоить его этой переменной.  
  
 Помимо классов, можно определять и использовать универсальные структуры, интерфейсы, процедуры и делегаты.  
  
 В следующей процедуре используется универсальный класс, определенный в [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], и создается его экземпляр.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Использование класса, который принимает параметр типа  
  
1.  В начале файла исходного кода, включают [оператор Imports (пространство имен .NET и тип)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) для импорта <xref:System.Collections.Generic?displayProperty=nameWithType> пространства имен. Это позволяет ссылаться на класс <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> без полного определения, чтобы его можно отличить от других классов очереди, таких как <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2.  Создайте объект обычным способом, но добавьте `(Of` `type``)` сразу после имени класса.  
  
     Следующий пример использует тот же класс (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) для создания двух объектов очереди, содержащих элементы различных типов данных. Он добавляет элементы в конец каждой очереди и затем удаляет и отображает элементы из начала каждой очереди.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>См. также

- [Типы данных](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
- [Универсальные типы в Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
- [Независимость от языка и независимые от языка компоненты](../../../../standard/language-independence-and-language-independent-components.md)  
- [Of](../../../../visual-basic/language-reference/statements/of-clause.md)  
- [Оператор Imports (пространство имен и тип .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
- [Практическое руководство. Определение класса, реализующего одинаковую функциональность для различных типов данных](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
- [Итераторы](../../../../visual-basic/programming-guide/concepts/iterators.md)
