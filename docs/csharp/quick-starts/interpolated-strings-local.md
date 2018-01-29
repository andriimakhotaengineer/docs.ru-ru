---
title: "Краткое руководство. Интерполированные строки в C#"
description: "В этом кратком руководстве, посвященном интерполированным строкам, вы напишете код C#, чтобы включить результат выражения в строку большего размера."
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 14185dd4e364f12756541ac6401d1c6ff3206fe9
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2018
---
# <a name="interpolated-strings"></a>Интерполированные строки

Это краткое руководство описывает, как использовать интерполированные строки в C#, чтобы вставить значения в одну строку вывода. Вы напишете код C# и сможете просмотреть результаты его компиляции и выполнения. Это краткое руководство содержит ряд занятий по вставке значений в строки и разнообразному форматированию этих значений.

Для работы с этим кратким руководством вам потребуется компьютер, который можно использовать для разработки. В руководстве по [началу работы с .NET за 10 минут](https://www.microsoft.com/net/core) содержатся инструкции по настройке локальной среды разработки на компьютерах Mac, Windows или Linux. Краткий обзор команд, которые будут использоваться, и ссылки на дополнительные сведения представлены в [вводной статье к руководствам по локальным средам](local-environment.md). 

## <a name="create-an-interpolated-string"></a>Создание интерполированной строки

Создайте каталог с именем **interpolated-quickstart**. Сделайте его текущим, выполнив следующую команду в окне консоли:

```console
dotnet new console -n interpolated -o .
```

Эта команда создает консольное приложение .NET Core в текущем каталоге.

Откройте файл **Program.cs** в любом редакторе и замените строку `Console.WriteLine("Hello World!");` следующим кодом, указав вместо `<name>` свое имя:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
Чтобы выполнить этот код, введите `dotnet run` в окне консоли. При запуске программы отображается одна строка, которая содержит ваше имя в приветствии. Строка, включенная в вызов метода <xref:System.Console.WriteLine%2A>, является *интерполированной*. Это похоже на шаблон, позволяющий создать одну строку (называемую *результирующей строкой*) из строки, содержащей внедренный код. Интерполированные строки особенно удобны при вставке значений в строку или сцеплении (объединении) строк. 
    
Этот простой пример содержит два элемента, обязательные для каждой интерполированной строки: 

- Строковый литерал, который начинается с символа `$`, стоящего до открывающей кавычки. Между символом `$` и знаком кавычки не должно быть пробелов. (Если вы хотите узнать, что при этом случится, вставьте пробел после символа `$`, сохраните файл и снова запустите программу, введя `dotnet run` в окне консоли. Компилятор C# отображает сообщение "Ошибка CS1056. Непредвиденный знак "$"".) 

- Одно или несколько *интерполированных выражений*. Интерполированное выражение обозначено открывающей и закрывающей фигурной скобкой (`{` и `}`). Вы можете указать внутри фигурных скобок любое выражение C#, возвращающее значение (включая `null`). 

Давайте рассмотрим еще несколько примеров интерполированных строк с другими типами данных.
    
## <a name="include-different-data-types"></a>Включение разных типов данных

В предыдущем разделе вы использовали интерполированную строку для вставки одной строки внутрь другой. Однако выражение интерполированной строки может относиться к любому типу данных. Давайте рассмотрим интерполированную строку со значениями нескольких типов данных. 
    
Приведенный ниже пример включает интерполированные выражения с объектом `Vegetable`, членом перечисления `Unit`, значением <xref:System.DateTime> и значением <xref:System.Decimal>. Замените весь код C# в редакторе следующим кодом, а затем используйте команду `console run`, чтобы запустить его:

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
{
   public enum Unit { item, pound, ounce, dozen };
   
   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```
    
Обратите внимание, что второе интерполированное выражение включает объект `item` в результирующую строку, которая выводится на консоль. В данном случае в результирующую строку вставляется строка "eggplant" (баклажан). Это вызвано тем, что если тип интерполированного выражения отличается от строки, компилятор C# делает следующее:

- Если интерполированное выражение равно `null`, оно возвращает пустую строку ("" или <xref:System.String.Empty?displayProperty=nameWithType>).

- Если интерполированное выражение не равно `null`, вызывается метод `ToString` для типа интерполированного выражения. Это можно проверить, закомментировав определение метода `Vegetable.ToString` в этом примере, для чего перед ним нужно поставить символ комментария (`//`). В выходных данных строка "eggplant" заменяется именем типа "Vegetable" (овощ), что является стандартным поведением метода <xref:System.Object.ToString?displayProperty=nameWithType>.   

В выходных данных этого примера дата является слишком точной (цена на баклажаны не меняется каждую секунду), а в значении цены не указана единица измерения валюты. В следующем разделе вы узнаете, как устранить эти проблемы, управляя форматом строк, возвращаемых интерполированными выражениями.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Управление форматированием интерполированных выражений

В предыдущем разделе мы вставили две неправильно отформатированные строки в результирующую строку. Первая была значением даты и времени, при этом допустимой была только дата. Вторая была ценой, в которой отсутствовала единица измерения валюты. Обе эти проблемы легко решить. Интерполированные выражения могут включать *строки формата*, управляющие форматированием определенных типов. Измените вызов `Console.WriteLine` из предыдущего примера, включив в него описатель формата для полей даты и цены, как показано в следующей строке:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
Задайте строку формата, указав ее после интерполированного выражения через точку с запятой. "d" — это [стандартная строка формата для даты и времени](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), представляющая краткий формат. "C2" — это [стандартная строка числового формата](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), представляющая число в виде денежной единицы с точностью два знака после запятой.

Некоторые типы в библиотеках .NET Standard поддерживают предопределенный набор строк формата. К ним относятся все числовые типы, а также типы даты и времени. Полный список типов, поддерживающих строки формата, см. в разделе [Строки формата и типы библиотек классов .NET](../../standard/base-types/formatting-types.md#stringRef) статьи [Типы форматирования в .NET](../../standard/base-types/formatting-types.md). Любой тип может поддерживать набор строк формата, кроме того, можно разрабатывать расширения пользовательского форматирования для существующих типов. Сведения о пользовательском форматировании n посредством реализации <xref:System.ICustomFormatter> см. в разделе [Настраиваемое форматирование с использованием интерфейса ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) статьи [Типы форматирования в .NET](../../standard/base-types/formatting-types.md).

Попробуйте изменить строки формата в текстовом редакторе, возвращаясь в программу после каждого изменения, чтобы узнать, как они влияют на форматирование даты и времени, а также числового значения. Измените "d" в `{date:d}` на "t" (чтобы отобразить краткий формат времени), "y" (чтобы отобразить год и месяц) и "yyyy" (чтобы отобразить год в виде четырехзначного числа). Измените "C2" в `{price:C2}` на "e" (для экспоненциального представления) и "F3" (чтобы получить числовое значение с тремя знаками после запятой).

Кроме форматирования, вы можете управлять шириной поля и выравниванием для строк, возвращаемых интерполированным выражением. В следующем разделе вы научитесь это делать.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Управление шириной поля и выравниванием для интерполированных выражений

Как правило, когда строка, возвращаемая интерполированным выражением, включается в результирующую строку, в ней нет начальных или конечных пробелов. Специально для экземпляров, в которых вы работаете с набором данных, интерполированные выражения позволяют задать ширину поля и его выравнивание. Чтобы увидеть это, замените весь код в текстовом редакторе следующим кодом, а затем введите `console run` для выполнения программы:
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
Имена авторов выровнены по левому краю, а названия их произведений — по правому. Вы можете указать выравнивание, добавив запятую (",") после выражения и назначив ширину поля. Если ширина поля является положительным числом, то поле выравнивается по правому краю:

```text
{expression, width}
```

Если ширина поля является отрицательным числом, то поле выравнивается по левому краю:

```text
{expression, -width}
```

Попробуйте удалить знаки "минус" из интерполированных выражений `{"Author",-25}` и `{title.Key,-25}`, а затем снова запустите пример, как показано в следующем коде:

```csharp
Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
```

На этот раз сведения об авторе выровнены по правому краю.

Вы можете совмещать ширину поля и строку формата в одном интерполированном выражении. Сначала идет ширина поля, за которой следует двоеточие, а затем — строка формата. Замените весь код внутри метода `Main` приведенным ниже кодом, который отображает три отформатированные строки с заданной шириной поля. Запустите программу, введя команду `dotnet run`.

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
Выходные данные выглядят следующим образом:

```console
1/11/2018            Hour 09                1,063.34 feet
```

Вы ознакомились с кратким руководством по интерполированным строкам. 
    
Вы можете продолжить обучение в своей среде разработки и перейти к краткому руководству по [массивам и коллекциям](arrays-and-collections.md).

Дополнительные сведения о работе с интерполированными строками см. в разделе [Интерполированные строки](../language-reference/keywords/interpolated-strings.md) справочника по C#.
