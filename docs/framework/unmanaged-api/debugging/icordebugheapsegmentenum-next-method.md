---
title: "Метод ICorDebugHeapSegmentEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 655bc404003c4af3aa2ba934ee192b378caf2f2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="07ced-102">Метод ICorDebugHeapSegmentEnum::Next</span><span class="sxs-lookup"><span data-stu-id="07ced-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="07ced-103">Возвращает заданное число [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) экземпляров, которые содержат сведения о областей памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="07ced-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ced-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07ced-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07ced-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="07ced-105">Parameters</span></span>  
 <span data-ttu-id="07ced-106">celt</span><span class="sxs-lookup"><span data-stu-id="07ced-106">celt</span></span>  
 <span data-ttu-id="07ced-107">[in] Количество сегментов, которые требуется получить.</span><span class="sxs-lookup"><span data-stu-id="07ced-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="07ced-108">сегменты</span><span class="sxs-lookup"><span data-stu-id="07ced-108">segments</span></span>  
 <span data-ttu-id="07ced-109">[out] Массив указателей, каждый из которых указывает на [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) объект, предоставляющий сведения об области памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="07ced-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="07ced-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="07ced-110">pceltFetched</span></span>  
 <span data-ttu-id="07ced-111">[out] Указатель на число [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) объектов, фактически извлеченных в `segments`.</span><span class="sxs-lookup"><span data-stu-id="07ced-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="07ced-112">Это значение может быть `null`, если параметр `celt` имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="07ced-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07ced-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="07ced-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ced-114">Требования</span><span class="sxs-lookup"><span data-stu-id="07ced-114">Requirements</span></span>  
 <span data-ttu-id="07ced-115">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ced-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ced-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07ced-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07ced-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07ced-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07ced-118">**Версии платформы .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07ced-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ced-119">См. также</span><span class="sxs-lookup"><span data-stu-id="07ced-119">See Also</span></span>  
 [<span data-ttu-id="07ced-120">Интерфейс ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="07ced-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="07ced-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="07ced-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)