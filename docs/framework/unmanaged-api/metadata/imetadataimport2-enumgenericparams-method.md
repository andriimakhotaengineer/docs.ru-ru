---
title: "Метод IMetaDataImport2::EnumGenericParams"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0e6a5dc6cd1d82a3ccd46b09e301a84f90a3f429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="e1151-102">Метод IMetaDataImport2::EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="e1151-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="e1151-103">Возвращает перечислитель для массива маркеров параметра универсального типа, связанный с указанным TypeDef или MethodDef, токен.</span><span class="sxs-lookup"><span data-stu-id="e1151-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1151-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e1151-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1151-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e1151-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e1151-106">[in, out] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="e1151-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="e1151-107">[in] Токен TypeDef или MethodDef, которого универсальные параметры, подлежащие перечислению.</span><span class="sxs-lookup"><span data-stu-id="e1151-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="e1151-108">[out] Массив универсальных параметров для перечисления.</span><span class="sxs-lookup"><span data-stu-id="e1151-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e1151-109">[in] Максимальное количество маркеров для размещения в `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="e1151-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="e1151-110">[out] Возвращенное число маркеров помещаются в `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="e1151-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1151-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e1151-111">Return Value</span></span>  
  
|<span data-ttu-id="e1151-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1151-112">HRESULT</span></span>|<span data-ttu-id="e1151-113">Описание</span><span class="sxs-lookup"><span data-stu-id="e1151-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e1151-114">`EnumGenericParams`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="e1151-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e1151-115">`phEnum`не имеет члена элементов.</span><span class="sxs-lookup"><span data-stu-id="e1151-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="e1151-116">В этом случае `pcGenericParams` имеет значение 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="e1151-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1151-117">Требования</span><span class="sxs-lookup"><span data-stu-id="e1151-117">Requirements</span></span>  
 <span data-ttu-id="e1151-118">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1151-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1151-119">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1151-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1151-120">**Библиотека:** используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1151-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1151-121">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1151-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1151-122">См. также</span><span class="sxs-lookup"><span data-stu-id="e1151-122">See Also</span></span>  
 [<span data-ttu-id="e1151-123">IMetaDataImport2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="e1151-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="e1151-124">IMetaDataImport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="e1151-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)