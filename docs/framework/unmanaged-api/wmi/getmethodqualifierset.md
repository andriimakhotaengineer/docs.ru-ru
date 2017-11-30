---
title: "Функция GetMethodQualifierSet (Справочник по неуправляемым API)"
description: "Функция GetMethodQualifierSet получает набор описателей этого метода."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79a19d3bb40dd4d435bd7cf97eb0b4071020648e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="eee7b-103">Функция GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="eee7b-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="eee7b-104">Извлекает квалификатор для конкретного метода.</span><span class="sxs-lookup"><span data-stu-id="eee7b-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="eee7b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eee7b-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="eee7b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="eee7b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="eee7b-107">[in] Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="eee7b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="eee7b-108">[in] Указатель на [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="eee7b-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="eee7b-109">[in] Имя метода.</span><span class="sxs-lookup"><span data-stu-id="eee7b-109">[in] The method  name.</span></span> <span data-ttu-id="eee7b-110">`wszMethod`должен указывать на допустимый `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="eee7b-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="eee7b-111">[out] Получает указатель интерфейса, обеспечивающего доступ к квалификаторы метода.</span><span class="sxs-lookup"><span data-stu-id="eee7b-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="eee7b-112">Параметр `ppQualSet` не может иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="eee7b-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="eee7b-113">Если возникает ошибка не возвращается новый объект и указатель устанавливается на `null`.</span><span class="sxs-lookup"><span data-stu-id="eee7b-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="eee7b-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eee7b-114">Return value</span></span>

<span data-ttu-id="eee7b-115">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файла заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="eee7b-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="eee7b-116">Константа</span><span class="sxs-lookup"><span data-stu-id="eee7b-116">Constant</span></span>  |<span data-ttu-id="eee7b-117">Значение</span><span class="sxs-lookup"><span data-stu-id="eee7b-117">Value</span></span>  |<span data-ttu-id="eee7b-118">Описание</span><span class="sxs-lookup"><span data-stu-id="eee7b-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="eee7b-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="eee7b-119">0x80041002</span></span> | <span data-ttu-id="eee7b-120">Указанный метод не существует.</span><span class="sxs-lookup"><span data-stu-id="eee7b-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="eee7b-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="eee7b-121">0x80041008</span></span> | <span data-ttu-id="eee7b-122">Параметр — `null`.</span><span class="sxs-lookup"><span data-stu-id="eee7b-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="eee7b-123">0</span><span class="sxs-lookup"><span data-stu-id="eee7b-123">0</span></span> | <span data-ttu-id="eee7b-124">Успешный вызов функции.</span><span class="sxs-lookup"><span data-stu-id="eee7b-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="eee7b-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="eee7b-125">Remarks</span></span>

<span data-ttu-id="eee7b-126">Эта функция создает оболочку для вызова [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) метод.</span><span class="sxs-lookup"><span data-stu-id="eee7b-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="eee7b-127">Вызов эта функция поддерживается только в том случае, если текущий объект является определение класса CIM.</span><span class="sxs-lookup"><span data-stu-id="eee7b-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="eee7b-128">Метод обработки не доступен для [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters, указывают на экземпляры CIM.</span><span class="sxs-lookup"><span data-stu-id="eee7b-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="eee7b-129">Так как каждый метод может иметь свой собственный квалификаторы [IWbemQualifierSet указатель](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) позволяет вызывающему объекту добавить, изменить или удалить эти квалификаторы.</span><span class="sxs-lookup"><span data-stu-id="eee7b-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="eee7b-130">Требования</span><span class="sxs-lookup"><span data-stu-id="eee7b-130">Requirements</span></span>  
<span data-ttu-id="eee7b-131">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eee7b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eee7b-132">**Заголовок:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="eee7b-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="eee7b-133">**Версии платформы .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eee7b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee7b-134">См. также</span><span class="sxs-lookup"><span data-stu-id="eee7b-134">See also</span></span>  
[<span data-ttu-id="eee7b-135">WMI и счетчиков производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="eee7b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)