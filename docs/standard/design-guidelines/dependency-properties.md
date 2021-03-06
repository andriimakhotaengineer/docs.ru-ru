---
title: Свойства зависимостей
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75c83dc75d1c86c89169fcc54220ced2a195bfbe
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079091"
---
# <a name="dependency-properties"></a>Свойства зависимостей
Свойства зависимостей (DP) — это обычное свойство, его значение сохраняется в хранилище свойств, а не сохраняя его в переменную типа (поле), например.  
  
 Вложенное свойство зависимостей является разновидностью свойства зависимости, смоделированных как статические методы Get и Set, представляющий «свойства», описывающий связи между объектами и их контейнеры (например, положение `Button` объект `Panel` контейнер).  
  
 **✓ DO** свойства для поддержки функций WPF, таких как стили, триггеры, привязки данных, анимации, динамические ресурсы и наследование предоставляет свойства зависимостей.  
  
## <a name="dependency-property-design"></a>Разработка свойств зависимостей  
 **✓ DO** наследовать от <xref:System.Windows.DependencyObject>, или один из его подтипов, при реализации свойств зависимостей. Тип предоставляет очень эффективную реализацию алгоритма хранилище свойств и автоматически поддерживает привязка данных WPF.  
  
 **✓ DO** предоставляют обычным свойством CLR и открытое статическое доступное только для чтения поле, хранением экземпляра <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> для каждого свойства зависимости.  
  
 **✓ DO** реализации свойств зависимостей, вызвав методы экземпляра <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> и <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** имя статического поля свойств зависимостей, формируемый имя свойства с «Свойство».  
  
 **X DO NOT** явным образом задать значения по умолчанию для свойства зависимостей в коде; установить их в метаданных.  
  
 Если явно задать свойство по умолчанию, это свойство может привести к определяется какие-либо неявные средства, такие как стили.  
  
 **X DO NOT** поместить код в методах доступа свойства отличное от стандартного кода для доступа к статическому полю.  
  
 Что код не будет выполняться, если свойству неявное средствами, такие как стили, так как задание стиля непосредственно использует статическое поле.  
  
 **X DO NOT** использует свойства зависимостей для хранения конфиденциальных данных. Публично можно получить доступ к свойствам даже частные зависимостей.  
  
## <a name="attached-dependency-property-design"></a>Разработка свойств вложенных зависимостей  
 Свойства зависимостей, описанные в предыдущем разделе представляют внутренние свойства объявляющего типа; например `Text` свойство является свойством `TextButton`, которой они объявлены. Специальный вид свойства зависимостей является подключенное свойство зависимости.  
  
 Классическим примером присоединенного свойства является <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> свойство. Свойство представляет позицию столбца кнопки (не сетки), но это актуально только если кнопка находится в сетке, поэтому он «подключен» к кнопкам, сеток.  
  
```xaml
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 Определение вложенного свойства выглядит главным образом, свойства обычная зависимость, за исключением того, что методы доступа являются статическими методами Get и Set:  
  
```csharp
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a>Проверка свойств зависимостей  
 Свойства часто реализуют так называемый проверки. Логика проверки выполняется, когда предпринята попытка изменить значение свойства.  
  
 К сожалению доступа к свойствам зависимостей, не может содержать произвольный код. Вместо этого логика проверки свойства зависимостей должны быть определены во время регистрации свойства.  
  
 **X DO NOT** поместите логику проверки для свойства зависимостей в методах доступа к свойствам. Вместо этого передайте обратный вызов проверки для `DependencyProperty.Register` метод.  
  
## <a name="dependency-property-change-notifications"></a>Уведомления об изменении свойств зависимостей  
 **X DO NOT** реализовать логику уведомления изменения в методы доступа для свойства зависимостей. Свойства зависимостей имеют средство уведомления встроенные изменение, необходимо использовать, указав обратный вызов уведомления изменения <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Приведение значения свойства зависимостей  
 Свойство приведение происходит, когда значение, указанное для метода задания свойства изменяется метод задания до фактически изменяется хранилище свойств.  
  
 **X DO NOT** реализовать логику приведение в методы доступа для свойства зависимостей.  
  
 Свойства зависимостей имеют встроенные приведения компонент, и он может использоваться, указав обратного приведения `PropertyMetadata`.  
  
 *Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*  
  
 *Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*  
  
## <a name="see-also"></a>См. также

- [Рекомендации по проектированию на основе Framework](../../../docs/standard/design-guidelines/index.md)  
- [Обычные шаблоны разработки](../../../docs/standard/design-guidelines/common-design-patterns.md)
