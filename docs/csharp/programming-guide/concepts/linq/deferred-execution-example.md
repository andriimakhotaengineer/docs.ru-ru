---
title: Пример отложенного выполнения (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0ad1ed2998cfbd612f7f2b60a0d15c7ffcef0daf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518479"
---
# <a name="deferred-execution-example-c"></a>Пример отложенного выполнения (C#)
В данном разделе показано влияние отложенного выполнения и отложенного вычисления на запросы LINQ to XML.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется порядок выполнения при использовании метода расширения, в котором применяется отложенное выполнение. В этом примере объявляется массив из трех строк. Затем в нем производится итерация по коллекции, возвращенной `ConvertCollectionToUpperCase`.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 В этом примере выводятся следующие данные:  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Обратите внимание, что во время итерации по коллекции, возвращенной `ConvertCollectionToUpperCase`, происходит получение каждого элемента из исходного массива строк и преобразование символов в верхний регистр до получения следующего элемента из исходного массива строк.  
  
 Видно, что весь массив строк не преобразуется в символы верхнего регистра, пока каждый элемент возвращенной коллекции не будет обработан циклом `foreach` в `Main`.  
  
 Следующий раздел учебника иллюстрирует объединение запросов в цепочки:  
  
-   [Пример связывания запросов (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>См. также

- [Учебник. Объединение запросов в цепочки (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
