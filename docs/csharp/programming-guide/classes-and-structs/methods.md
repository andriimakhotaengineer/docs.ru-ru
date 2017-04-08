---
title: "Методы (руководство по программированию на C#) | Документы Майкрософт"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e44ef58e85fee164ab3b8be73a35083bd44c5df1
ms.lasthandoff: 03/13/2017

---
# <a name="methods-c-programming-guide"></a>Методы (Руководство по программированию на C#)
Метод — это блок кода, содержащий ряд инструкций. Программа инициирует выполнение инструкций, вызывая метод и указывая все аргументы, необходимые для этого метода. В C# все инструкции выполняются в контексте метода. Метод Main является точкой входа для каждого приложения C#, и он вызывается общеязыковой средой выполнения (CLR) при запуске программы.  
  
> [!NOTE]
>  В этом разделе рассматриваются названные методы. Сведения об анонимных функциях см. в разделе [Анонимные функции](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Сигнатуры методов  
 Методы объявляются в [классе](../../../csharp/language-reference/keywords/class.md) или в [структуре](../../../csharp/language-reference/keywords/struct.md) путем указания уровня доступа, такого как `public` или `private`, необязательных модификаторов, таких как `abstract` или `sealed`, возвращаемого значения, имени метода и всех параметров этого метода. Все эти части вместе представляют собой сигнатуру метода.  
  
> [!NOTE]
>  Тип возврата метода не является частью сигнатуры метода в целях перегрузки метода. Однако он является частью сигнатуры метода при определении совместимости между делегатом и методом, который он указывает.  
  
 Параметры метода заключаются в скобки и разделяются запятыми. Пустые скобки указывают, что параметры методу не требуются. Этот класс содержит три следующих метода.  
  
 [!code-cs[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>Метод доступа  
 Вызов метода в объекте аналогичен доступу к полю. После имени объекта добавьте точку, имя метода и круглые скобки. Аргументы перечисляются в этих скобках и разделяются запятыми. Таким образом, методы класса `Motorcycle` могут вызываться, как показано в следующем примере:  
  
 [!code-cs[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>Параметры методов и Аргументы  
 Определение метода задает имена и типы всех необходимых параметров. Когда вызывающий код вызывает метод, он предоставляет конкретные значения, называемые аргументами, для каждого параметра. Аргументы должны быть совместимы с типом параметра, но имя аргумента (если есть), используемое в вызывающем коде, не обязательно должно совпадать с именем параметра, указанным в методе. Например:  
  
 [!code-cs[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Передача по ссылке и передача по значению  
 По умолчанию при передаче в метод типа значения вместо самого объекта передается его копия. Поэтому изменения в аргументе не оказывают влияния на исходную копию в вызывающем методе. Вы можете передавать тип значения по ссылке с помощью ключевого слова ref. Дополнительные сведения см. в разделе [Передача параметров типа значения](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Список встроенных типов значений см. в разделе [Таблица типов значений](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 При передаче в метод объекта ссылочного типа передается ссылка на этот объект. То есть метод получает не сам объект, а аргумент, который указывает расположение объекта. При изменении члена объекта с помощью этой ссылки это изменение отражается в аргументе в вызывающем методе, даже если объект передается по значению.  
  
 Ссылочный тип создается с помощью ключевого слова `class` , как показано в следующем примере.  
  
 [!code-cs[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 Теперь, если передать объект, основанный на этом типе, в метод, то будет передана ссылка на объект. В следующем примере объект типа `SampleRefType` передается в метод `ModifyObject`.  
  
 [!code-cs[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 В этом примере, в сущности, делается то же, что и в предыдущем примере, — аргумент по значению передается в метод. Но поскольку здесь используется ссылочный тип, результат будет другим. В данном случае в методе `ModifyObject` изменено поле `value` параметра `obj`, а также изменено поле `value` аргумента, `rt`в методе `TestRefType` . В качестве выходных данных метод `TestRefType` отображает 33.  
  
 Дополнительные сведения о передаче ссылочных типов по ссылке и по значению см. в разделах [Передача параметров ссылочного типа](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) и [Ссылочные типы](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Методы могут возвращать значение вызывающему объекту. Если тип возврата, указываемый перед именем метода, не `void`, этот метод может возвращать значение с помощью ключевого слова `return` . Инструкция с ключевым словом `return` , за которым следует значение, соответствующее типу возврата, будет возвращать это значение объекту, вызвавшему метод. Ключевое слове `return` также останавливает выполнение метода. Если тип возврата — `void`, инструкцию `return` без значения по-прежнему можно использовать для завершения выполнения метода. Без ключевого слова `return` этот метод будет останавливать выполнение при достижении конца блока кода. Методы с типом возврата, отличным от void, должны использовать ключевое слово `return` для возврата значения. Например, в следующих двух методах ключевое слово `return` используется для возврата целочисленных значений.  
  
 [!code-cs[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 Чтобы использовать значение, возвращаемое из метода, вызывающий метод может применять сам вызов метода везде, где будет достаточно значения того же типа. Можно также назначить возвращаемое значение переменной. Например, следующие два примера кода достигают одной и той же цели.  
  
 [!code-cs[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-cs[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 Использование локальной переменной, в данном случае `result`, для сохранения значения является необязательным. Это может улучшить читаемость кода или может оказаться необходимым, если нужно сохранить исходное значение аргумента для всей области метода.  
  
 Возврат многомерного массива из метода M, изменяющего содержимое массива, не является необходимым, если вызывающая функция передала массив в метод M. Итоговый массив можно вернуть из метода M в целях соблюдения правильного стиля или модели передачи значений, но делать это не обязательно.  Причина отсутствия необходимости в возврате измененного массива в том, что C# передает все ссылочные типы по значению, а значением ссылки на массив является указатель на массив. В методе M любые изменения содержимого массива отслеживаются любым кодом, имеющим ссылку на массив, как показано в приведенном ниже примере.  
  
```csharp  
static void Main(string[] args)  
        {  
            int[,] matrix = new int[2, 2];  
            FillMatrix(matrix);  
            // matrix is now full of -1  
        }  
  
        public static void FillMatrix(int[,] matrix)  
        {  
            for (int i = 0; i < matrix.GetLength(0); i++)  
            {  
                for (int j = 0; j < matrix.GetLength(1); j++)  
                {  
                    matrix[i, j] = -1;  
                }  
            }  
        }  
  
```  
  
 Дополнительные сведения см. в разделе [return](../../../csharp/language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Асинхронные методы  
 С помощью функции async можно вызывать асинхронные методы, не прибегая к использованию явных обратных вызовов или ручному разделению кода между несколькими методами или лямбда-выражениями. Функция async появилась в [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs_dev11_long_md.md)].  
  
 Если пометить метод с помощью модификатора [async](../../../csharp/language-reference/keywords/async.md), можно использовать в этом методе оператор [await](../../../csharp/language-reference/keywords/await.md). Когда управление достигает выражения await в асинхронном методе, управление возвращается вызывающему объекту и выполнение метода приостанавливается до завершения выполнения ожидающей задачи. После завершения задачи можно возобновить выполнение в методе.  
  
> [!NOTE]
>  Асинхронный метод возвращается в вызывающий объект, когда он встречает первый ожидаемый объект, выполнение которого еще не завершено, или когда выполнение асинхронного метода доходит до конца — в зависимости от того, что происходит раньше.  
  
 Асинхронный метод может иметь тип возвращаемого значения <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> или void. Тип возврата void в основном используется для определения обработчиков событий, где требуется тип возврата void. Асинхронный метод, который возвращает тип void, не может быть ожидающим. Вызывающий объект метода, возвращающего значение типа void, не может перехватывать исключения, которые выдает этот метод.  
  
 В следующем примере `DelayAsync` является асинхронным методом с типом возвращаемого значения <xref:System.Threading.Tasks.Task%601>. `DelayAsync` имеет инструкцию `return`, которая возвращает целое число. Поэтому объявление метода `DelayAsync` должно иметь тип возврата `Task<int>`. Поскольку тип возврата — `Task<int>`, вычисление выражения `await` в `DoSomethingAsync` создает целое число, как показывает следующая инструкция: `int result = await delayTask`.  
  
 В следующем примере метод `startButton_Click` служит примером асинхронного метода с типом возврата void. Поскольку `DoSomethingAsync` является асинхронным методом, задача для вызова `DoSomethingAsync` должна быть ожидаемой, как показывает следующая инструкция: `await DoSomethingAsync();`. Метод `startButton_Click` должен быть определен с модификатором `async` , так как этот метод имеет выражение `await` .  
  
 [!code-cs[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 Асинхронный метод не может объявить все параметры [ref](../../../csharp/language-reference/keywords/ref.md) или [out](../../../csharp/language-reference/keywords/out.md), но может вызвать методы, которые имеют такие параметры.  
  
 Дополнительные сведения об асинхронных методах см. в разделах [Асинхронное программирование с использованием ключевых слов async и await](../../../csharp/programming-guide/concepts/async/index.md), [Поток управления в асинхронных программах](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md) и [Асинхронные типы возврата](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>Определения текста выражений  
 Часто используются определения методов, которые просто немедленно возвращаются с результатом выражения или которые имеют единственную инструкцию в тексте метода.  Для определения таких методов существует сокращенный синтаксис с использованием `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Если метод возвращает `void` или является асинхронным методом, то текст метода должен быть выражением инструкции (так же, как при использовании лямбда-выражений).  Свойства и индексаторы должны быть только для чтения, и вы не должны использовать ключевое слово `get` метода доступа.  
  
## <a name="iterators"></a>Итераторы  
 Итератор выполняет настраиваемую итерацию по коллекции, например по списку или массиву. Итератор использует оператор [yield return](../../../csharp/language-reference/keywords/yield.md) для возврата всех элементов по одному. Когда достигается оператор [yield return](../../../csharp/language-reference/keywords/yield.md), текущее расположение в коде запоминается. При следующем вызове итератора выполнение возобновляется с этого места.  
  
 Итератор вызывается из клиентского кода с помощью оператора [foreach](../../../csharp/language-reference/keywords/foreach-in.md) .  
  
 Тип возвращаемого значения итератора может быть <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> или <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Дополнительные сведения см. в разделе [Итераторы](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="c-language-specification"></a>Спецификация языка C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>См. также  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)   
 [Классы и структуры](index.md)   
 [Модификаторы доступа](access-modifiers.md)   
 [Статические классы и члены статических классов](static-classes-and-static-class-members.md)   
 [Наследование](inheritance.md)   
 [Абстрактные и запечатанные классы и члены классов](abstract-and-sealed-classes-and-class-members.md)   
 [params](../../../csharp/language-reference/keywords/params.md)   
 [return](../../../csharp/language-reference/keywords/return.md)   
 [out](../../../csharp/language-reference/keywords/out.md)   
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [Передача параметров](passing-parameters.md)