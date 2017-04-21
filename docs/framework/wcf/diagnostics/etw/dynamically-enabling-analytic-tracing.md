---
title: "Динамическое включение аналитического отслеживания | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Динамическое включение аналитического отслеживания
Средства, поставляемые в составе ОС Windows, позволяют включать или отключать динамическую трассировку с использованием трассировки событий Windows \(ETW\). Аналитическая трассировка может быть включена и отключена динамически, без изменения файла Web.config приложения или перезапуска службы для всех служб [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]. Это дает возможность не останавливать работу приложения, создающего события трассировки.  
  
 Параметры трассировки [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] могут быть настроены таким же способом. Например, можно, не останавливая приложение, изменить степень серьезности со значения **Ошибки** на **Сведения**. Это можно сделать с помощью следующих средств.  
  
-   **Logman** \- средство командной строки, предназначенное для настройки, управления и запроса данных трассировки.[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Logman Create Trace](http://go.microsoft.com/fwlink/?LinkId=165426) и [Logman Update Trace](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **EventViewer** \- графическое средство Windows для просмотра результатов трассировки.[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Службы WCF и средство отслеживания событий для Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) и [Просмотр событий](http://go.microsoft.com/fwlink/?LinkId=165428)  
  
-   **Системный монитор** \- графическое средство управления Windows, которое использует счетчики для наблюдения за счетчиками трассировки и ее влиянием на производительность.[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Создание набора сборщиков данных вручную](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### Ключевые слова  
 С использованием класса <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> трассировка сообщений платформы .NET Framework в общем случае подлежит фильтрации по степени серьезности \(«Ошибки», «Предупреждения», «Сведения»\). Трассировка событий Windows поддерживает концепцию уровня серьезности, а также вводит новый, более гибкий механизм фильтрации по ключевым словам. Ключевые слова \- это произвольные текстовые значения, которые позволяют событиям трассировки предоставлять дополнительный контекст о значении события.  
  
 Для аналитической трассировки [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] каждый из уровней трассировки содержит два типа ключевых слов. Во\-первых, каждое событие имеет одно или несколько ключевых слов сценариев. Они указывают на сценарий, для которого предназначено данное событие. Существует три ключевых слова сценариев. Каждое из них предназначено для определенной цели, как показано в следующей таблице. Фильтрация по ключевым словам может быть изменена динамически, без нарушения работы службы [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. Это означает, что можно динамически изменить текущий сценарий трассировки и количество собираемых сведений. Например, можно установить `HealthMonitoring` в значение `Troubleshooting` и увеличить частоту событий трассировки.  
  
|Ключевое слово|Описание|  
|--------------------|--------------|  
|`HealthMonitoring`|Очень простая минимальная трассировка, которая позволяет наблюдать за активностью службы.|  
|`EndToEndMonitoring`|Для поддержки трассировки потока сообщений используются события.|  
|`Troubleshooting`|Более частые события о точках расширяемости [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
 Вторая группа ключевых слов определяет, каким из компонентов [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] создано данное событие.  
  
|Ключевое слово|Описание|  
|--------------------|--------------|  
|`UserEvents`|События, которые созданы пользовательским кодом, а не [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|События, которые созданы средой выполнения [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
|`ServiceHost`|События, которые созданы узлом службы.|  
|`WCFMessageLogging`|События ведения журнала сообщений [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
## См. также  
 [Службы WCF и средство отслеживания событий для Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)