---
title: Получение шаблонов элементов управления, поддерживающих модель автоматизации пользовательского интерфейса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: b0bc694148dbd91cd9e942a3f051aea9362fc150
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511480"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Получение шаблонов элементов управления, поддерживающих модель автоматизации пользовательского интерфейса
> [!NOTE]
>  Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 В этом разделе показано, как получить объекты шаблона элемента управления из [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] элементов.  
  
### <a name="obtain-all-control-patterns"></a>Получение всех шаблонов элементов управления  
  
1.  Получить <xref:System.Windows.Automation.AutomationElement> шаблоны элементов управления которого вас интересуют.  
  
2.  Вызовите <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> для получения всех шаблонов элементов управления в элементе.  
  
> [!CAUTION]
>  Настоятельно рекомендуется, чтобы клиент не использовал <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Производительность может значительно снизиться, так как этот метод вызывает метод <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> внутренне для каждого существующего шаблона элемента управления. Если это возможно, клиент должен вызывать <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> для основных интересующих шаблонов.  
  
### <a name="obtain-a-specific-control-pattern"></a>Получение конкретного шаблона элемента управления  
  
1.  Получить <xref:System.Windows.Automation.AutomationElement> шаблоны элементов управления которого вас интересуют.  
  
2.  Вызовите <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> или <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> для запроса определенного шаблона. Эти методы похожи, но если шаблон не найден, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> вызывает исключение, и <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> возвращает `false`.  
  
## <a name="example"></a>Пример  
 В следующем примере извлекается <xref:System.Windows.Automation.AutomationElement> для элемента списка и получает <xref:System.Windows.Automation.SelectionItemPattern> от этого элемента.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>См. также  
 [Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
