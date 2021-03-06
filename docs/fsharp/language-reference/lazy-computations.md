---
title: Отложенные вычисления (F#)
description: 'Узнайте, как F # отложенные вычисления могут повысить производительность приложений и библиотек.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676523"
---
# <a name="lazy-computations"></a>Отложенные вычисления

*Отложенные вычисления* — это вычисления, которые выполняются не сразу, но когда требуется результат. Это может помочь повысить производительность кода.

## <a name="syntax"></a>Синтаксис

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Примечания

В приведенном выше синтаксисе *выражение* приведен код, который вычисляется только в том случае, если результат является обязательным, и *идентификатор* является значение, в котором хранится результат. Значение имеет тип [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), где фактический тип, используемый для `'T` определяется на основе результата выражения.

Отложенные вычисления позволяют повысить производительность, ограничивая выполнение вычислений только ситуаций, в которых потребуется результат.

Чтобы принудительно выполнить вычисления, вызовите метод `Force`. `Force` приводит к выполнению должна выполнять только один раз. Последующие вызовы `Force` возвращают же результат, но не выполняется никакой код.

Следующий код иллюстрирует использование отложенного вычисления и использование `Force`. В этом коде, тип `result` — `Lazy<int>`и `Force` возвращает метод `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Отложенные вычисления, но не `Lazy` введите, также используется для последовательностей. Дополнительные сведения см. в разделе [последовательностей](sequences.md).

## <a name="see-also"></a>См. также

- [Справочник по языку F#](index.md)
- [Lazyextensions-модуль](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
