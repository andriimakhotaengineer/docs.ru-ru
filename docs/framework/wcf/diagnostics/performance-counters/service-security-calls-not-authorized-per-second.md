---
title: 'Служба: количество неавторизованных вызовов системы безопасности в секунду'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f2c921991f059d7dfe5661dfe688ec9675d0d5fe
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625546"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Служба: количество неавторизованных вызовов системы безопасности в секунду
Имя счетчика: Security Calls Not Authorized Per Second  
  
## <a name="description"></a>Описание  
 Число входящих сообщений в секунду, надлежаще защищенных и поступивших от допустимого пользователя, не авторизованного для выполнения определенных задач.  
  
 Значение этого счетчика увеличивается, когда метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> возвращает значение `false`.  
  
 Этот счетчик является счетчиком производительности типа [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), значение которого вычисляется по следующей формуле.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
