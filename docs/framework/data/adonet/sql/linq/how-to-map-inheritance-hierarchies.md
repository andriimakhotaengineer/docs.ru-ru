---
title: Практическое руководство. Сопоставление иерархий наследования
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 627baf61902877390b0b2c88bf25438cb26c6491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355365"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Практическое руководство. Сопоставление иерархий наследования
Чтобы реализовать сопоставление наследования в [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], в корневом классе иерархии наследования необходимо указать атрибуты и свойства атрибутов, как описано в следующих шагах. С помощью Visual Studio разработчики могут использовать [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] для сопоставления иерархии наследования. В разделе [как: Настройка наследования с помощью реляционного конструктора объектов](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
>  Особые атрибуты или свойства подклассов не требуются. Обратите особое внимание на то, что подклассы не имеют атрибута <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Сопоставление иерархий наследования  
  
1.  Добавьте к корневому классу атрибут <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
2.  Кроме того, в корневом классе необходимо добавить атрибут <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> для каждого класса в структуре иерархии.  
  
3.  Определите свойство <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> для каждого атрибута <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
     Это свойство содержит значение, которое отображается в столбце <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> таблицы базы данных и указывает, к какому классу или подклассу принадлежит эта строка данных.  
  
4.  Добавьте также для каждого атрибута <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> свойство <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.  
  
     Данное свойство содержит значение, которое указывает, на какой класс или подкласс указывает значение ключа.  
  
5.  Добавьте свойство <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> только к одному атрибуту <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.  
  
     Данное свойство используется для обозначения *резервной* сопоставление, когда значение дискриминатора из таблицы базы данных не соответствует ни одному <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> значение в сопоставлениях наследования.  
  
6.  Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> к атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
     Это свойство означает, что данный столбец содержит значение <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
## <a name="example"></a>Пример  
  
> [!NOTE]
>  Если вы используете Visual Studio, можно использовать [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] для настройки наследования. В разделе [как: Настройка наследования с помощью реляционного конструктора объектов](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 В следующем примере кода определяется корневой класс `Vehicle` и выполняются указанные выше шаги с целью описания иерархии для [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>См. также  
 [Поддержка наследования](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)  
 [Практическое руководство. Настройка классов сущностей с использованием редактора кода](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
