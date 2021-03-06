---
title: Активация на основе конфигурации в IIS и WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: d15202a7d34f3246cd7679687b6a510252fe3541
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594045"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Активация на основе конфигурации в IIS и WAS
Обычно при размещении службы Windows Communication Foundation (WCF) в Internet Information Services (IIS) или службы активации процессов Windows (WAS), необходимо указать SVC-файла. SVC-файл содержит имя службы, а также дополнительную пользовательскую фабрику узла службы. С помощью этого дополнительного файла добавляются служебные данные по управлению. Возможность активации на основе конфигурации снимает требование по наличию SVC-файла и, следовательно, по наличию связанных служебных данных.  
  
## <a name="configuration-based-activation"></a>Активация на основе конфигурации  
 Активация на основе конфигурации принимает метаданные, которые используются для размещения в SVC-файле, и помещает их в файл Web.config. В рамках <`serviceHostingEnvironment`> имеется элемент <`serviceActivations`> элемента. В рамках <`serviceActivations`> элемент один или несколько <`add`> элементов, по одному для каждой размещенной службы. <`add`> Содержит атрибуты, которые позволяют задавать относительный адрес для службы и тип службы или фабрику узла службы. В следующем примере конфигурации показано, каким образом используется этот раздел.  
  
> [!NOTE]
>  Каждый <`add`> элемент должен задавать службы или атрибут factory. Можно указать и атрибут службы, и атрибут фабрики.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Такой код, показанный в файле Web.config, позволяет поместить исходный код службы в каталог App_Code приложения или откомпилированную сборку в каталог Bin приложения.  
  
> [!NOTE]
>  -   При использовании активации на основе конфигурации, встроенный программный код в SVC-файлах не поддерживается.  
> -   `relativeAddress` Атрибута необходимо задать относительный адрес такие как "\<вложенный каталог > / service.svc» или «~ /\<второстепенных Sub-Directory/service.svc».  
> -   Если зарегистрирован относительный адрес, который не содержит известного расширения имени, связанного с WCF, то будет создано исключение конфигурации.  
> -   Относительный адрес указывается относительно корневого каталога виртуального приложения.  
> -   Поскольку модель конфигурации имеет иерархическую структуру, относительный адрес, который зарегистрирован на уровне компьютера и узла, наследуется виртуальными приложениями.  
> -   Регистрация в файле конфигурации имеет более высокий приоритет, чем параметры в SVC-файле, XAMLX-файле, XOML-файле и других файлах.  
> -   Все символы обратной косой черты «\» в URI, отправляемых в IIS/WAS, автоматически преобразуются в символы косой черты «/». Если добавляемый относительный адрес содержит символ «\», а в IIS отправлен URI, который использует относительный адрес, то символ обратной косой черты преобразуется в символ косой черты и IIS не может сопоставить его с относительным адресом. Службы IIS отправляют сведения трассировки, которые указывают, что соответствие не найдено.  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Размещение служб](../../../../docs/framework/wcf/hosting-services.md)  
 [Общие сведения о размещении служб рабочих процессов](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Функции размещения фабрики приложений Windows Server](https://go.microsoft.com/fwlink/?LinkId=201276)
