---
title: Встроенная конфигурация
ms.date: 03/30/2017
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
ms.openlocfilehash: e76c019d9fc1b416e6fa8175a70b5fd01d9ff53e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084797"
---
# <a name="built-in-configuration"></a>Встроенная конфигурация
Этот образец показывает использование и настройку хранилища экземпляров рабочих процессов SQL. Хранилище экземпляров рабочих процессов SQL - это реализация хранилища экземпляров на основе SQL Server. Она позволяет экземпляру загружать свое состояние из базы данных SQL Server или SQL Server Express, либо сохранять состояние в этой базе данных.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к (загрузка страницы) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Подробные сведения об образце  
 Этот образец состоит из рабочего процесса, реализующего службу счета. После вызова метода запуска службы служба начинает считать от 0 до 59. Значение счетчика увеличивается каждые 2 секунды. Рабочий процесс сохраняется после каждого отсчета.  
  
 Рабочий процесс подсчета является резидентным в узле службы рабочих процессов. Метод `Main` программы создает экземпляр узла службы рабочих процессов, в котором размещается рабочий процесс подсчета. Он определяет конечные точки, по которым можно получить доступ к рабочему процессу подсчета. После этого он определяет поведение хранилища экземпляров рабочих процессов SQL, которое используется для настройки экземпляра рабочего процесса SQL. Затем программа создает клиент, который вызывает метод запуска рабочего процесса подсчета.  
  
 После запуска программы счетчик автоматически начинает увеличиваться. Учтите, что на загрузку экземпляра и настройку хранилища экземпляров рабочих процессов SQL может уйти несколько секунд. Дополнительные сведения о хранилище экземпляров рабочих процессов, см. в разделе [Store экземпляра рабочего процесса SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Образец состоит из двух частей:  
  
1.  InstanceStore1 показывает настройку <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> с использованием кода C# (см. файл Program.cs).  
  
2.  InstanceStore2 показывает настройку <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> с использованием XML (см. файл App.config).  
  
 Настраивать поведение хранилища экземпляров рабочих процессов SQL можно с помощью следующих параметров:  
  
-   Установите свойство `HostLockRenewalPeriod`. Это время определяет интервал, в течение которого узел обновляет владение блокировкой выполняемых им экземпляров. Сведения о блокировке хранятся в хранилище экземпляров. Если владение не обновляется в течение двух интервалов, определенных в `HostLockRenewalPeriod`, экземпляр считается прерванным. Если другой узел <xref:System.ServiceModel.Activities.WorkflowServiceHost> выполняет тот же рабочий процесс и подключен к тому же хранилищу экземпляров (на той же или на другой машине), он восстанавливает экземпляр. (Восстановление экземпляра находится вне рамок обсуждения для данного образца.)  
  
-   Установите свойство `RunnableInstancesDetectionPeriod`. Этот период определяет интервал, в течение которого узел выполняет опрос в поисках экземпляров, которые стали готовы к запуску. Экземпляры могут стать готовыми к запуску, если произойдет одно из следующих событий.  
  
    -   Истекает срок действия устойчивого таймера (<xref:System.Activities.Statements.Delay>).  
  
    -   Еще один узел пропускает тактовый импульс `HostLockRenewal` (например, вследствие сбоя компьютера) и экземпляр восстанавливается.  
  
-   Установите свойство `InstanceCompletionAction`. Это свойство, если для него установлено значение `DeleteNothing`, сохраняет завершенные экземпляры в хранилище экземпляров; если же задано значение `DeleteAll`, экземпляры удаляются из хранилища после завершения. Обратите внимание, что  
  
    > [!NOTE]
    >  завершение узла нажатием клавиши ВВОД перед завершением подсчета не приводит к завершению экземпляра рабочего процесса.  
  
-   Установите свойство `InstanceLockedExceptionAction`. Эта настройка определяет, что должен сделать узел, если требуется загрузить экземпляр, блокированный другим узлом. Возможны следующие варианты.  
  
    -   Если задано значение `NoRetry`: Не предпринимать повторных попыток загрузки и возвратить узлу `InstanceLockedException`.  
  
    -   Если задано значение `BasicRetry`: Повтор попыток загрузки экземпляра. Повторные попытки включаются в расписание по простому линейному алгоритму (например, повторная попытка через каждые 5 секунд).  
  
    -   Если задано значение `AggressiveRetry`: Повтор попыток загрузки экземпляра. Повторные попытки включаются в расписание по агрессивному алгоритму с экспоненциальной задержкой.  
  
-   Установка параметра Encoding (кодировки). Этот параметр определяет способ сохранения состояния экземпляра в хранилище экземпляров рабочего процесса SQL. Возможны следующие варианты.  
  
    -   Состояние экземпляра сжимается с применением алгоритма сжатия GZip.  
  
    -   Состояние экземпляра не сжато.  
  
#### <a name="to-use-this-sample"></a>Использование этого образца  
  
1.  Откройте командную строку [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] от имени учетной записи администратора, если имеются разрешения на это.  
  
2.  Перейдите в каталог образцов (\WF\Basic\Persistence\BuiltInConfiguration\CS) и запустите команду CreateInstanceStore.cmd.  
  
3.  Если права администратора не доступны, создайте имя входа SQL Server. Перейдите к `Security`, **имена входа**. Щелкните правой кнопкой мыши **имена входа** и создайте новое имя входа.  
  
4.  Добавьте пользователя из списка ACL к роли SQL. Откройте **баз данных**, **InstanceStore**, **безопасности**. Щелкните правой кнопкой мыши **пользователей** и выберите **новых пользователей**. Задайте **имя входа** для пользователя, созданного на предыдущем шаге. Добавьте пользователя в предопределенную роль базы данных **System.Activities.DurableInstancing.InstanceStoreUsers** (и других). Обратите внимание, что пользователь может уже существовать (например, пользователь dbo).  
  
5.  Откройте файл InstanceStore.sln в среде [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] и выполните сборку решения нажатием сочетания клавиш CTRL+SHIFT+B.  
  
6.  В [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], перейдите в каталог образца bin\debug соответствующие (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), щелкните правой кнопкой мыши InstanceStore.exe и выберите **Запуск от имени администратора**. Этот образец необходимо запускать с правами администратора, так как он открывает прослушиватель каналов.  
  
7.  Если хранилище экземпляров создано в базе данных, отличной от локального экземпляра SQL Server Express, необходимо обновить строку подключения базы данных (`const string ConnectionString` в файле Program.cs проекта InstanceStore1, и атрибут `connectionString` в файле App.config проекта InstanceStore2) в образце и перекомпилировать образец.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Проверка правильности работы образца  
  
1.  Во время работы образца запустите среду SQL Server Management Studio.  
  
2.  В **обозревателя объектов**выберите **баз данных**, **InstanceStore**, **таблиц**, а затем  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Щелкните правой кнопкой мыши **InstanceTable** и выберите **выделить 1000 верхних строк**.  
  
4.  Обратите внимание на наличие новой записи и что **срока блокировки** изменяется каждые 5 секунд (щелкните на панели задач **Execute** кнопку, чтобы обновить запрос). Это происходит потому, что параметру **период обновления блокировки узла** до 5.  
  
5.  Обратите внимание, что после завершения подсчета запись в таблице экземпляров удаляется. Это происходит потому, что параметру **действие завершения экземпляра** для **DeleteAll**.  
  
6.  Нажмите клавишу ВВОД, чтобы завершить ведущее приложение рабочего процесса и обратите внимание, что **LockOwnersTable** удаляется.  
  
#### <a name="to-uninstall-the-sample"></a>Удаление образца  
  
1.  Запустите файл RemoveInstanceStore.cmd в каталоге образцов (\WF\Basic\Persistence\BuiltInConfiguration).  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>См. также  
 [Образцы размещения AppFabric и сохраняемости](https://go.microsoft.com/fwlink/?LinkId=193961)
