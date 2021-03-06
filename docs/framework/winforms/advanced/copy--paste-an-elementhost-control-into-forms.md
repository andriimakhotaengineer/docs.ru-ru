---
title: Пошаговое руководство. Копирование и вставка элемента интерфейса ElementHost в отдельную форму Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 55b426fbe95bac269183a649ecd839175a8cbdda
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778478"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>Пошаговое руководство. Копирование и вставка элемента интерфейса ElementHost в отдельную форму Windows Forms
В этом пошаговом руководстве описывается, как скопировать элемент управления Windows Presentation Foundation (WPF) из одной формы Windows Forms в другую.  
  
 В руководстве выполняются следующие задачи:  
  
-   создание проекта;  
  
-   копирование элемента управления WPF.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание проекта Windows Forms.  
  
> [!NOTE]
>  При размещении содержимого WPF поддерживаются только проекты C# и Visual Basic.  
  
#### <a name="to-create-the-project"></a>Создание проекта  
  
-   Создание нового проекта приложения Windows Forms в Visual Basic или Visual C# с именем `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>Копирование элемента управления WPF  
 После добавления в проект элемента управления WPF его можно скопировать в другие формы проекта.  
  
#### <a name="to-copy-a-wpf-control"></a>Копирование элемента управления WPF  
  
1.  Добавьте в решение новый проект WPF <xref:System.Windows.Controls.UserControl>. Используйте имя по умолчанию для этого типа элемента управления (`UserControl1.xaml`). Дополнительные сведения см. в разделе [Пошаговое руководство: Создание нового содержимого WPF в формах Windows Forms во время разработки](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Выполните построение проекта.  
  
3.  Откройте `Form1` в конструкторе Windows Forms.  
  
4.  Из **элементов**, перетащите экземпляр `UserControl1` на форму.  
  
     Экземпляр `UserControl1` разместится в новом элементе управления <xref:System.Windows.Forms.Integration.ElementHost> с именем `elementHost1`.  
  
5.  Выбрав элемент управления `elementHost1`, нажмите клавиши CTRL+C, чтобы скопировать его в буфер обмена.  
  
6.  Добавьте в проект новую форму Windows Forms. Используйте имя по умолчанию для этого типа формы (`Form2`).  
  
7.  При открытой в конструкторе Windows Forms форме `Form2` нажмите клавиши CRTL+V, чтобы вставить в форму копию `elementHost1`.  
  
     Скопированный элемент управления также имеет имя `elementHost1`, так как это закрытое поле класса `Form2`. Конфликта имен с `elementHost1` в классе `Form1` не возникает.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Миграция и взаимодействие систем](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Использование элементов управления WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Проектирование XAML в Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
