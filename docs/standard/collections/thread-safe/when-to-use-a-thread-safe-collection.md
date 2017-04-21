---
title: "Преимущества использования потокобезопасных коллекций | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "потокобезопасные коллекции, время обновления"
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Преимущества использования потокобезопасных коллекций
На платформе [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] доступны пять новых типов коллекций, которые специально разработаны для поддержки многопотоковых операций добавления и удаления.  Для достижения потокобезопасности эти новые типы используют различные типы эффективных механизмов синхронизации с блокировкой и без блокировки.  Синхронизация добавляет к операции издержки.  Значения издержек зависят от используемого типа синхронизации, выполняемого типа операции и других факторов, например, количества потоков, которые одновременно пытаются получить доступ к коллекции.  
  
 В некоторых сценариях издержки синхронизации незначительны и позволяют многопотоковым вариантам выполняться значительно быстрее и обеспечивают лучшую масштабируемость, чем в случае потоконебезопасного эквивалента при защите с помощью внешней блокировки.  В других сценариях издержки могут вызвать ситуацию, когда потокобезопасный вариант выполняется и масштабируется примерно также и даже более медленно, чем потоконебезопасная версия типа с внешней блокировкой.  
  
 В следующих подразделах приводятся общие рекомендации по использованию потокобезопасной коллекции и потоконебезопасного эквивалента, который содержит заданную пользователем блокировку для операций чтения и записи.  Так производительность может зависеть от множества факторов, рекомендации нехарактерны и необязательно являются допустимыми во всех обстоятельствах.  Если производительность имеет важное значение, то лучшим способом для определения используемого типа коллекции является измерение производительности на основе обычной конфигурации компьютера и нагрузке.  В данном документе используются следующие термины.  
  
 *Чистый сценарий "производитель\-получатель"*  
 Все заданные потоки либо добавляют элементы, либо удаляют их, но не то и другое вместе.  
  
 *Смешанный сценарий "производитель\-получатель"*  
 Все заданные потоки добавляют элементы или удаляют их.  
  
 *Ускорение*  
 Ускорение производительности алгоритма одного типа относительно другого типа в этом же сценарии.  
  
 *Масштабируемость*  
 Увеличение в производительности, которое пропорционально количеству ядер в компьютере.  Масштабируемый алгоритм выполняется быстрее на компьютере у которого восемь ядер, чем на компьютере у которого два ядра.  
  
## ConcurrentQueue\(T\) и Queue\(T\)  
 В чистых сценариях "производитель\-получатель", когда время обработки каждого элемента очень мало \(несколько инструкций\), класс <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> может предложить незначительный рост производительности по сравнению с классом <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>, который содержит внешнюю блокировку.  В этом сценарии класс <xref:System.Collections.Concurrent.ConcurrentQueue%601> выполняется лучше, когда один выделенный поток помещается в очередь, а другой выделенный поток удаляется из очереди.  Если это правило не применяется, класс <xref:System.Collections.Generic.Queue%601> может даже выполняться немного быстрее, чем класс <xref:System.Collections.Concurrent.ConcurrentQueue%601> на компьютерах, у которых есть несколько ядер.  
  
 Когда время обработки составляет 500 FLOPS \(операций с плавающей запятой\) или больше, то правило двух потоков не применяется к классу <xref:System.Collections.Concurrent.ConcurrentQueue%601>, который имеет очень хорошую масштабируемость.  Класс <xref:System.Collections.Generic.Queue%601> в данном сценарии не имеет хорошей масштабируемости.  
  
 В смешанных сценариях "производитель\-получатель", когда время обработки очень мало, класс <xref:System.Collections.Generic.Queue%601>, который имеет внешнюю блокировку, масштабируется лучше, чем класс <xref:System.Collections.Concurrent.ConcurrentQueue%601>.  Однако, если время обработки имеет значение приблизительно равное 500 FLOPS и выше, то класс <xref:System.Collections.Concurrent.ConcurrentQueue%601> масштабируется лучше.  
  
## ConcurrentStack и Stack  
 В чистых сценариях "производитель\-получатель", когда время обработки каждого элемента очень мало, класс <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> и класс <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>, который имеет внешнюю блокировку, вероятно будут выполняться одинаково с одним выделенным потоком на добавление и одним выделенным потоком на извлечение.  Однако по мере увеличения числа потоков, производительность снижается у обоих типов, так как увеличивается число конфликтных ситуаций, и класс <xref:System.Collections.Generic.Stack%601> может выполняться лучше, чем класс <xref:System.Collections.Concurrent.ConcurrentStack%601>.  Если время обработки имеет значение приблизительно равное 500 FLOPS и выше, то оба типа масштабируются примерно одинаково.  
  
 В смешанных сценариях "производитель\-получатель" класс <xref:System.Collections.Concurrent.ConcurrentStack%601> имеет большее ускорение для небольших и больших рабочих нагрузок.  
  
 Использование методов <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> и <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> может значительно снизить время доступа.  
  
## ConcurrentDictionary и Dictionary  
 В общем случае, используйте класс <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> в любом сценарии, в котором выполняется добавление и обновление ключей и значений одновременно из множества потоков.  В сценариях, которые включают частные операции обновления и относительно редкие операции чтения, класс <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, в общем случае, обеспечивает немного лучшую производительность.  В сценариях, которые включают частные операции чтения и относительно редкие операции обновления, класс <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, в общем случае, имеет значительно большее ускорение на компьютерах, которые имеют несколько ядер.  
  
 В сценариях, которые включают частые обновления, можно увеличить степень параллелизма в классе <xref:System.Collections.Concurrent.ConcurrentDictionary%602> и затем провести оценку, чтобы увидеть увеличилась ли производительность на компьютерах, которые имеют несколько ядер.  При изменение уровня параллелизма исключите, насколько это возможно, глобальные операции.  
  
 Если выполняются только операции чтения ключа или значений, класс <xref:System.Collections.Generic.Dictionary%602> имеет большее ускорение, так как если словарь не изменяется каким\-либо потоком, то синхронизация не требуется.  
  
## Класс ConcurrentBag  
 В чистых сценариях "производитель\-получатель" класс <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> вероятно будет выполняться более медленно, чем один из типов параллельных коллекций.  
  
 В смешанных сценариях "производитель\-получатель" класс <xref:System.Collections.Concurrent.ConcurrentBag%601> в общем случае имеет большее ускорение и большую масштабируемость, чем все остальные типы параллельных коллекций для небольших и больших рабочих нагрузок.  
  
## Класс BlockingCollection  
 Если требуются семантики границ и блокировок, класс <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> вероятно будет выполняться быстрее, чем все другие пользовательские реализации.  Он также поддерживает гибкую обработку исключений и операций отмены, перечисления.  
  
## См. также  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Потокобезопасные коллекции](../../../../docs/standard/collections/thread-safe/index.md)   
 [Parallel Programming](../../../../docs/standard/parallel-programming/index.md)