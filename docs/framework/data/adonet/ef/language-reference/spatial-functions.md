---
title: Пространственные функции
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676153"
---
# <a name="spatial-functions"></a>Пространственные функции
Форматов литералов для пространственных типов не имеется. Однако можно использовать канонические функции Entity Framework, вызываемые с помощью строк в формате известного текстового представления. Например, следующий вызов функции создает точку геометрии.  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [Методы SpatialEdmFunctions](https://msdn.microsoft.com/library/hh749531.aspx) странице перечисляются все Пространственные канонические методы Entity Framework. Щелкните интересующий метод, чтобы посмотреть, какие параметры должны быть переданы функции.
