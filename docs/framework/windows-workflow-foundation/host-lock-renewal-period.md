---
title: "Период обновления блокировки узла | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Период обновления блокировки узла
Свойство **Период обновления блокировки узла** хранилища экземпляров рабочих процессов SQL позволяет задать период времени, в течение которого узел обновляет блокировку экземпляра рабочего процесса.Блокировка действует в течение периода обновления блокировки узла \+ 30 секунд.Если узел не обновляет блокировку в течение этого периода времени \(иными словами, не продлевает аренду\), срок действия блокировки прекращается и поставщик сохраняемости разблокирует экземпляр.Это свойство имеет значение типа TimeSpan в формате «чч:мм:сс».Минимальное допустимое значение: «00:00:01» \(1 секунда\).По умолчанию значение этого свойства равно «00:00:30» \(30 секунд\).  
  
 Это свойство важно в сценариях с отказом узла службы рабочего процесса, прежде чем он разблокирует принадлежащий ему экземпляр службы рабочего процесса.В этом сценарии блокировка экземпляра службы рабочего процесса в базе данных сохраняемости удаляется поставщиком сохраняемости, когда заканчивается срок действия блокировки. Другой узел службы рабочего процесса, работающий на том же самом или на другом компьютере фермы серверов, может получить блокировку и загрузить экземпляр службы рабочего процесса в память, чтобы возобновить его выполнение из последнего сохраненного состояния.  
  
 Если задать этому свойству большее значение, экземпляр службы рабочего процесса будет заблокирован в базе данных сохраняемости на более длительный срок, что задержит восстановление экземпляра из последнего сохраненного состояния.Если задать в этом свойстве более короткий интервал, новый экземпляр узла службы рабочего процесса быстро получит отказавший экземпляр службы рабочего процесса, но возрастет нагрузка на узел службы рабочего процесса и базу данных SQL Server.  
  
 В хранилище экземпляров рабочих процессов SQL есть внутренняя задача, которая периодически запускается и выявляет экземпляры с истекшей блокировкой.Обнаружив такие экземпляры, она помещает их в таблицу RunnableInstances, чтобы узел рабочего процесса мог получить их и запустить.