---
title: "Общие сведения о параметрах приложений | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ApplicationsSettingsOverview"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "параметры приложения [Windows Forms], сведения о параметрах приложения"
  - "динамические свойства"
  - "настройки пользователя, отслеживание"
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Общие сведения о параметрах приложений
В этом разделе описывается создание и хранение параметров приложения и пользователей.  
  
 Параметры приложения в Windows Forms позволяют легко создавать, хранить и поддерживать настраиваемые приложения и параметры пользователей на клиентском компьютере. С помощью параметров приложения Windows Forms можно хранить не только данные приложения, например строки подключений к базам данных, но и пользовательские данные, такие как предпочтения пользователя приложения. Используя Visual Studio или настраиваемый управляемый код, можно создавать новые параметры, читать их и записывать на диск, связывать их со свойствами в формах и проверять данные параметров до загрузки и сохранения.  
  
 Параметры приложения позволяют разработчикам сохранять состояние своих приложений с помощью очень небольшого объема кода. Они являются заменой динамических свойств в предыдущих версиях [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Параметры приложения содержат много улучшений по сравнению с динамическими свойствами, которые доступны только для чтения. Кроме того, в динамических свойствах используется позднее связывание, и для них требуется дополнительное программирование. Классы динамических свойств были сохранены в [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], но они являются лишь классами\-оболочками для классов параметров приложения.  
  
## Что такое параметры приложения  
 Приложениям Windows Forms часто требуются важные для их выполнения данные, которые, однако, нежелательно включать непосредственно в код приложения. Если приложение использует веб\-службу или сервер базы данных, эти сведения можно хранить в отдельном файле, чтобы в будущем была возможность изменить их без перекомпиляции. Аналогичным образом приложению может потребоваться сохранить данные, относящиеся к текущему пользователю. В большинстве приложений, например, применяются пользовательские предпочтения, определяющие внешний вид и поведение приложения.  
  
 Параметры приложения отвечают обеим потребностям, предоставляя простой способ хранения параметров приложения и пользователей на клиентском компьютере. С помощью Visual Studio или редактора кода можно определить значение параметра, указав его имя, тип данных и область действия \(приложение или пользователь\). Вы можете даже поместить связанные параметры в именованные группы для повышения простоты и удобочитаемости кода. После определения эти параметры сохраняются и считываются обратно в память автоматически во время выполнения. Подключаемая архитектура позволяет изменять механизм сохранения, однако по умолчанию используется локальная файловая система.  
  
 Параметры приложения работают путем сохранения данных в формате XML в различных файлах конфигурации \(CONFIG\-файлах\) в зависимости от того, что является областью действия параметра — приложение или пользователь. В большинстве случаев параметры приложения доступны только для чтения. Так как они содержат сведения для программы, обычно их не нужно перезаписывать. Параметры пользователей, напротив, можно и считывать, и записывать во время выполнения, даже если приложение работает в режиме частичного доверия. Дополнительные сведения о частичном доверии см. в разделе [Security in Windows Forms Overview](../../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
 Параметры хранятся в виде XML\-фрагментов в файлах конфигурации. Параметры приложения представлены элементом `<application.Settings>`. Обычно они размещаются в файле *app*.exe.config, где *app* — имя основного исполняемого файла. Параметры пользователей представлены элементом `<userSettings>` и помещаются в файле *user*.config, где *user* — имя пользователя, запустившего приложение. Файл *app*.exe.config необходимо развернуть вместе с приложением. Архитектура параметров создает файлы *user*.config по запросу, когда приложение в первый раз сохраняет параметры для этого пользователя. Вы можете также определить блок `<userSettings>` в файле *app*.exe.config, чтобы предоставить значения по умолчанию для параметров пользователя.  
  
 Пользовательские элементы управления могут сохранять собственные параметры с помощью реализации интерфейса <xref:System.Configuration.IPersistComponentSettings>, который предоставляет метод <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A>. Элемент управления <xref:System.Windows.Forms.ToolStrip> Windows Forms реализует этот интерфейс, чтобы сохранить положение панелей инструментов и их элементов между сеансами приложения. Дополнительные сведения о пользовательских элементах управления и параметрах приложения см. в разделе [Application Settings for Custom Controls](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md).  
  
## Ограничения параметров приложения  
 Нельзя использовать параметры приложения в неуправляемых приложениях, которые размещаются в среде [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Параметры не будут работать в таких средах, как надстройки Visual Studio, C\+\+ для Microsoft Office, элементы управления, размещенные в Internet Explorer, или надстройки и проекты Microsoft Outlook.  
  
 В настоящее время нельзя выполнить привязку к некоторым свойствам в Windows Forms. Наиболее важным примером является свойство <xref:System.Windows.Forms.Form.ClientSize%2A>, так как привязка к этому свойству вызовет непредсказуемое поведение во время выполнения. Как правило, такого рода проблем можно избежать путем программного сохранения и загрузки этих параметров.  
  
 Параметры приложения не имеют встроенных средств для автоматического шифрования информации. Никогда не следует хранить конфиденциальные данные, такие как пароли к базам данных, в виде открытого текста. Если требуется хранить такие сведения, то разработчик приложения обязан обеспечить надлежащую безопасность хранения. Если нужно хранить строки подключений, рекомендуется использовать встроенную систему безопасности Windows и не прибегать к таким средствам, как жесткое программирование паролей в URL\-адресах. Для получения дополнительной информации см. [Управление доступом для кода и ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
## Начало работы с параметрами приложения  
 Если используется Visual Studio, вы можете определить параметры в конструкторе Windows Forms с помощью свойства **\(ApplicationSettings\)** в окне **Свойства**. При таком определении параметров Visual Studio автоматически создает пользовательский управляемый класс\-оболочку, связывающий каждый параметр со свойством класса. Visual Studio также обеспечивает привязку параметра к свойству в форме или элементе управления таким образом, чтобы параметры элемента управления автоматически восстанавливались при отображении содержащей его формы и автоматически сохранялись при закрытии формы.  
  
 Если требуется более детальное управление параметрами, можно определить собственный класс\-оболочку параметров приложения. Для этого нужно создать класс, производный от <xref:System.Configuration.ApplicationSettingsBase>, добавить свойства, соответствующие каждому параметру, и применить к ним специальные атрибуты. Дополнительные сведения о создании классов\-оболочек см. в разделе [Application Settings Architecture](../../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
 Вы можете также использовать класс <xref:System.Windows.Forms.Binding> для программной привязки параметров к свойствам в формах и элементах управления.  
  
## См. также  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.SettingsProvider>   
 <xref:System.Configuration.LocalFileSettingsProvider>   
 <xref:System.Configuration.IPersistComponentSettings>   
 [How to: Validate Application Settings](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)   
 [Управление параметрами приложения \(.NET\)](../Topic/Managing%20Application%20Settings%20\(.NET\).md)   
 [How To: Read Settings at Run Time With C\#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)   
 [Using Application Settings and User Settings](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [Application Settings Architecture](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)   
 [Application Settings for Custom Controls](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)