---
title: "Установка службы очередей сообщений (MSMQ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Установка службы очередей сообщений (MSMQ)
В процедурах ниже показана методика установки очереди сообщений 4.0 и очереди сообщений 3.0.  
  
> [!NOTE]
>  Очередь сообщений 4.0 не входит в [!INCLUDE[wxp](../../../../includes/wxp-md.md)] и [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### Установка Message Queuing 4.0 в Windows Server 2008 или Windows Server 2008 R2  
  
1.  Щелкните **Функции** в диспетчере сервера.  
  
2.  Щелкните **Добавить функции** в области справа под разделом **Сводка по функциям**.  
  
3.  Разверните в появившемся окне **Очередь сообщений**.  
  
4.  Разверните **Службы очереди сообщений**.  
  
5.  Щелкните **Интеграция служб директории** \(для компьютеров, подключенных к домену\), затем щелкните **Поддержка HTTP**.  
  
6.  Щелкните **Далее**, затем щелкните **Установить**.  
  
#### Установка очереди сообщений 4.0 в Windows 7 или Windows Vista  
  
1.  Откройте **панель управления**.  
  
2.  Щелкните **Программы** и затем в разделе **Программы и функции** щелкните **Включить и выключить функции Windows**.  
  
3.  Разверните сервер очереди сообщений Microsoft \(MSMQ\), разверните ядро сервера очереди сообщений Microsoft \(MSMQ\) и затем отметьте флажками установку следующих функций очереди сообщений:  
  
    -   MSMQ Доменные службы Active Directory \(для компьютеров, подключенных к домену\).  
  
    -   Поддержка MSMQ HTTP.  
  
4.  Нажмите кнопку **OК**.  
  
5.  При появлении запроса на перезагрузку компьютера нажмите кнопку **ОК** для завершения установки.  
  
#### Установка Message Queuing 3.0 в Windows XP или Windows Server 2003  
  
1.  Откройте **панель управления**.  
  
2.  Выберите **Добавить компоненты Windows** в окне **Установка и удаление программ**.  
  
3.  Выберите очередь сообщений и щелкните **Сведения**.  
  
    > [!NOTE]
    >  При работе в [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] выберите сервер приложений для доступа к очереди сообщений.  
  
4.  Удостоверьтесь, что на странице сведений выбрана функция поддержки MSMQ HTTP.  
  
5.  Нажмите кнопку **ОК** для выхода из страницы, содержащей сведения. Затем нажмите кнопку **Далее**.Завершите установку.  
  
6.  При появлении запроса на перезагрузку компьютера нажмите кнопку **ОК** для завершения установки.  
  
## См. также  
 [Инструкции по установке](../../../../docs/framework/wcf/samples/set-up-instructions.md)