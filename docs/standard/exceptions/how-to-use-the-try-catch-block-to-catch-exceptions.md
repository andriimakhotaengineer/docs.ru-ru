---
title: Практическое руководство. Использование пробного блока и блока перехвата для перехвата исключений
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2018
ms.locfileid: "45618091"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Использование блока try/catch для перехвата исключений

Поместите фрагмент кода, который может выдавать исключения, в `try` блок, а код, который обрабатывает исключения, — в блок `catch`. Блок `catch` — это последовательность операторов, начинающаяся с ключевого слова `catch`, за которым следует тип исключения и требуемое действие.

В следующем примере кода блок `try`/`catch` используется для перехвата возможного исключения. Метод `Main` содержит блок `try` с оператором <xref:System.IO.StreamReader>, который открывает файл данных `data.txt` и записывает строку из этого файла. Следующий блок `try` — это блок `catch`, который перехватывает все исключения, поступающие из блока `try`.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Среда CLR перехватывает исключения, которые не перехватываются блоком catch. В зависимости от настроек среды выполнения появляется диалоговое окно отладки, работа программы завершается и отображается диалоговое окно со сведениями об исключении либо ошибка выводится в STDERR.

> [!NOTE] 
> Исключение может быть вызвано практически любой строкой кода, особенно те исключения, которые вызываются самой средой CLR, например <xref:System.OutOfMemoryException>. Большинству приложений не требуется обрабатывать эти исключения, но вы должны помнить об этом при написании библиотек, предназначенных для других пользователей. Рекомендации о том, когда следует помещать код в блок Try, см. в разделе о [лучших методиках обработки исключений](best-practices-for-exceptions.md).

## <a name="see-also"></a>См. также

- [Исключения](index.md)
