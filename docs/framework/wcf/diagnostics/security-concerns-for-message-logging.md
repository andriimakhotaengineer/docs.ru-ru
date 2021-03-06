---
title: Проблемы безопасности при ведении журналов сообщений
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6da641ec5da20c80f4c1034ded8a3be7d036b5a8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185984"
---
# <a name="security-concerns-for-message-logging"></a>Проблемы безопасности при ведении журналов сообщений
В этом разделе описываются способы защиты конфиденциальных данных от раскрытия в журналах сообщений, а также в событиях, формируемых посредством ведения журнала сообщений.  
  
## <a name="security-concerns"></a>Проблемы безопасности  
  
### <a name="logging-sensitive-information"></a>Регистрация конфиденциальных сведений  
 Windows Communication Foundation (WCF) не изменяет никакие данные в приложении заголовки и текст. WCF также не отслеживает персональные данные в приложении заголовках или тексте сообщения.  
  
 Когда регистрация сообщений включена, персональные данные в заголовках, зависящих от приложения (такие как строка запроса), и в теле сообщения (такие как номер кредитной карты), могут быть видимы в журналах. За надлежащее управление доступом к файлам конфигурации и журналов отвечает специалист, выполняющий развертывание приложения. Если требуется, чтобы подобные сведения не были видимы, необходимо отключить регистрацию или фильтровать часть данных (если предполагается доступ к журналам других лиц).  
  
 Следующие советы помогут предотвратить непреднамеренное раскрытие содержимого файла журнала.  
  
-   Убедитесь, что файлы журналов защищены с помощью списков управления доступом (ACL), как в сценарии с размещением на веб-сервере, так и в сценарии с резидентной службой.  
  
-   Выберите расширение файла, которое нельзя легко получить с помощью веб-запроса. Например, расширение XML безопасным не является. Список расширений, которые могут быть получены, можно найти в руководстве по администрированию Internet Information Services (IIS).  
  
-   Задайте абсолютный путь к местоположению файла журнала, которое должно находиться за пределами общедоступного каталога vroot веб-сервера во избежание доступа к нему третьих лиц с помощью веб-браузера.  
  
 По умолчанию ключи и персональные данные (personally identifiable information, PII), такие как имя пользователя и пароль, не регистрируются трассировкой и не указываются в заносимых в журнал сообщениях. Администратор компьютера может, тем не менее, с помощью атрибута `enableLoggingKnownPII` в элементе `machineSettings` файла Machine.config разрешить приложениям, выполняющимся на компьютере, регистрировать известные персональные данные (PII). Следующая конфигурация показывает, как это сделать.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Специалист, выполняющий развертывание приложения, может затем с помощью атрибута `logKnownPii` в файле App.config или Web.config включить регистрацию персональных данных следующим образом:  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
```  
  
 Регистрация PII включена, только когда оба параметра имеют значение `true`. Такое сочетание из двух ключей позволяет регистрировать известные PII для каждого приложения.  
  
> [!IMPORTANT]
>  В [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] для флагов `logEntireMessage` и `logKnownPii` необходимо задать значение `true` в файле Web.config или файле App.config, чтобы включить регистрацию персональных данных, как показано в следующем примере: `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Необходимо иметь в виду, что при задании в файле конфигурации двух или более пользовательских источников считываются только атрибуты первого источника. Остальные атрибуты не учитываются. Это значит, что в случае следующего файла App.config PII не регистрируются для обоих источников, несмотря на то что для второго источника явно включена регистрация персональных данных.  
  
```xml  
<system.diagnostics>  
   <sources>  
      <source name="System.ServiceModel.MessageLogging"  
              logKnownPii="false">  
              <listeners>  
                 <add name="messages"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\messages.svclog" />  
              </listeners>  
            </source>  
      <source name="System.ServiceModel"   
              logKnownPii="true">  
              <listeners>  
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Если элемент `<machineSettings enableLoggingKnownPii="Boolean"/>`<xref:System.Configuration.ConfigurationErrorsException> присутствует за пределами файла Machine.config, система вызывает исключение.  
  
 Изменения вступают в силу только после запуска или перезапуска приложения. Когда оба атрибута имеют значение `true`, при запуске регистрируется событие. Событие также регистрируется, если атрибут `logKnownPii` имеет значение `true`, а атрибут `enableLoggingKnownPii` имеет значение `false`.  
  
 Администратор компьютера и специалист, выполняющий развертывание приложения, должны быть предельно осторожными при использовании этих двух переключателей. Если регистрация PII включена, ключи контроля доступа и персональные данные заносятся в журналы. Если она отключена, конфиденциальные и зависящие от приложения данные все равно регистрируются в составе заголовков и тел сообщений. Более подробное рассмотрение конфиденциальности и защиты персональных данных от раскрытия, см. в разделе [конфиденциальность пользователей](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  В неправильно сформированных сообщениях PII не скрываются. Такие сообщения регистрируются «как есть», без каких-либо изменений. Упомянутые выше атрибуты никак на это не влияют.  
  
### <a name="custom-trace-listener"></a>Пользовательский прослушиватель трассировки  
 Добавление пользовательского прослушивателя трассировки на источник трассировки «Ведение журнала сообщений» должно быть привилегией исключительно администратора. Это связано с тем, что пользовательские прослушиватели могут быть настроены злоумышленниками на удаленную отправку сообщений, что может привести к разглашению конфиденциальных сведений. Кроме того, если пользовательский прослушиватель настроен на отправку сообщений по линии связи, например в удаленную базу данных, необходимо обеспечить надлежащее управление доступом к журналам сообщений на удаленной машине.  
  
## <a name="events-triggered-by-message-logging"></a>События, активируемые регистрацией сообщений  
 Ниже приведен исчерпывающий список событий, формируемых регистрацией событий.  
  
-   Регистрация сообщений включена: это событие создается при включении регистрации сообщений в конфигурации или посредством инструментария WMI. Содержание события: "Регистрация сообщений включена. Секретные сведения могут регистрироваться без шифрования, даже если при передаче они были зашифрованы, например, тексты сообщений".  
  
-   Регистрация сообщений отключена: это событие создается при отключении регистрации сообщений в конфигурации или посредством инструментария WMI. Содержание события: "Регистрация сообщений отключена".  
  
-   Регистрация известных PII отключена: это событие создается при включении регистрации известных персональных данных. Это происходит, когда `enableLoggingKnownPii` атрибут в `machineSettings` файла Machine.config имеет значение `true`и `logKnownPii` атрибут `source` в файле App.config или Web.config имеет значение `true`.  
  
-   Регистрация известных PII запрещена: это событие создается, когда Регистрация известных персональных данных не разрешена. Это происходит при `logKnownPii` атрибут `source` в файле App.config или Web.config имеет значение `true`, но `enableLoggingKnownPii` атрибут в `machineSettings` файла Machine.config имеет значение `false`. Исключение не возникает.  
  
 Эти события можно просмотреть с помощью средства просмотра событий, входящего в состав Windows. Дополнительные сведения об этом см. в разделе [ведение журнала событий](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>См. также  
 [Ведение журналов сообщений](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Проблемы безопасности и полезные советы при трассировке](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
