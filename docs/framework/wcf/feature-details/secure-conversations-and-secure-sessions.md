---
title: Безопасные диалоги и безопасные сеансы
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d44a132f4bc4982ba0df437a56859de1a6fe441a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194755"
---
# <a name="secure-conversations-and-secure-sessions"></a>Безопасные диалоги и безопасные сеансы
Это функция Windows Communication Foundation (WCF) является возможность установления безопасных сеансов между двумя конечными точками, которые проверяют подлинность друг друга и согласуйте шифрования и цифровой подписи процесса. Например, конечная точка службы может требовать, чтобы клиентская конечная точка передавала для проверки подлинности маркер безопасности, основанный на сертификате X.509. После завершения проверки подлинности клиента конечная точка службы возвращает клиенту маркер контекста безопасности (SCT), который затем используется для обеспечения безопасности всех последующих сообщений в сеансе. Установление такого безопасного сеанса повышает эффективность набора сообщений, которыми обмениваются эти две конечные точки, так как маркер SCT имеет симметричный ключ. При создании цифровой подписи или шифровании набора данных асимметричные ключи, на которых основаны сертификаты X.509, требуют значительно большей вычислительной мощности, чем симметричные ключи.  
  
 Политика начальной загрузки (определенные в разделе 6.2.7 [WS-SecurityPolicy](https://go.microsoft.com/fwlink/?LinkId=99817) standard) содержит утверждения безопасности сообщений, используемый для защиты канала и проверки подлинности клиента до обмена RST/SCT и RSTR/SCT. У некоторых стандартных привязок WCF `Security.Message.EstablishSecurityContext` используется свойство, управляющим использованием безопасного диалога. При использовании пользовательских привязок начальная загрузка указывается путем вложения элементов безопасной привязки, либо с помощью [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) в файле конфигурации или вызвав <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> в коде.  
  
 Дополнительные сведения о сеансах см. в разделе [с использованием сеансов](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>См. также  
 [Сеансы, экземпляры и параллелизм](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Практическое руководство. Создание службы, для которой требуются сеансы](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
