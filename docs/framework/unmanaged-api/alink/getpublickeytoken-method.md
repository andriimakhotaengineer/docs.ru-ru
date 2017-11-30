---
title: "Метод GetPublicKeyToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetPublicKeyToken
api_location: alink.dll
api_type: COM
f1_keywords: GetPublicKeyToken
helpviewer_keywords: GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5f41c8088f095802cf35239afab279d6324adb55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="f5140-102">Метод GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="f5140-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="f5140-103">Возвращает токен открытого ключа для заданного файла ключа или контейнер ключа.</span><span class="sxs-lookup"><span data-stu-id="f5140-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5140-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5140-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5140-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="f5140-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="f5140-106">Имя файла ключа.</span><span class="sxs-lookup"><span data-stu-id="f5140-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="f5140-107">Имя контейнера ключа.</span><span class="sxs-lookup"><span data-stu-id="f5140-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="f5140-108">Адрес, где будет храниться ключ.</span><span class="sxs-lookup"><span data-stu-id="f5140-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="f5140-109">Указывает размер в байтах буфера, обозначенном `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="f5140-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="f5140-110">По возвращении содержит фактическое число байтов, используемых.</span><span class="sxs-lookup"><span data-stu-id="f5140-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5140-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f5140-111">Return Value</span></span>  
 <span data-ttu-id="f5140-112">Возвращает значение S_OK, если метод выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="f5140-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5140-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f5140-113">Requirements</span></span>  
 <span data-ttu-id="f5140-114">Требуется alink.h.</span><span class="sxs-lookup"><span data-stu-id="f5140-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5140-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f5140-115">See Also</span></span>  
 [<span data-ttu-id="f5140-116">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="f5140-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f5140-117">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="f5140-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f5140-118">ALink-интерфейс API</span><span class="sxs-lookup"><span data-stu-id="f5140-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)