---
title: Кэширование канала и операция Send
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503819"
---
# <a name="channel-caching-with-send"></a>Кэширование канала и операция Send
Объект <xref:System.ServiceModel.Activities.SendMessageChannelCache> позволяет пользователям использовать различные уровни кэширования канала для действий <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.SendParametersContent>. Кэширование на уровне экземпляра включено по умолчанию. Данный образец иллюстрирует перечисленные далее возможности.  
  
1.  Совместное использование <xref:System.ServiceModel.Activities.SendMessageChannelCache> в домене приложений.  
  
2.  Отключение кэширования канала.  
  
3.  Совместное использование <xref:System.ServiceModel.Activities.SendMessageChannelCache> экземплярами рабочих процессов на узле <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Демонстрации  
 Расширение <xref:System.ServiceModel.Activities.SendMessageChannelCache>, действия <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> и <xref:System.ServiceModel.Activities.SendReply>.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1.  Загрузите решение проекта в среду [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] и постройте проект.  
  
2.  Запустите приложение EchoWorkflowService, созданное в папке «\EchoWorkflowService\bin\debug».  
  
3.  Запустите приложение EchoWorkflowClient, созданное в папке «.\EchoWorkflowClient\bin\debug».  
  
4.  Клиент вызывает операцию Echo применительно к службе и печатает результаты. После того как результаты распечатаны, нажмите клавишу ВВОД, чтобы закрыть клиент и службу.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
