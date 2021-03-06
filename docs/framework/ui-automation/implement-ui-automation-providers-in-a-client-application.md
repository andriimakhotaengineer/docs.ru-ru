---
title: Реализация поставщиков UI Automation в в приложении клиента
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 53459316a86d49adc4df3c9659b7e280be81e44c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509013"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Реализация поставщиков UI Automation в в приложении клиента
> [!NOTE]
>  Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 В этом разделе содержится пример кода, демонстрирующий реализацию клиентского поставщика автоматизации пользовательского интерфейса в приложении.  
  
 Это происходит редко. Чаще всего клиентское приложение автоматизации пользовательского интерфейса использует поставщики на стороне сервера или поставщики на стороне клиента, которые находятся в библиотеке DLL.  
  
## <a name="example"></a>Пример  
 В следующем примере кода реализуется простой поставщик для окна консоли. Этот код не имеет никаких полезных функциональных возможностей, но он предназначен для демонстрации основных действий по настройке поставщика в коде клиента и его регистрации с помощью метода <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о поставщиках автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Регистрация сборки поставщика на стороне клиента](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)  
 [Создание поставщика автоматизации пользовательского интерфейса на стороне клиента](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [Реализация клиентского поставщика автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
