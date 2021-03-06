---
title: Метод ICorDebugController::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7a95f09d1baebed65bae994550431d88ba0dfc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412475"
---
# <a name="icordebugcontrollerterminate-method"></a>Метод ICorDebugController::Terminate
Завершает процесс с помощью указанного кода выхода.  
  
> [!NOTE]
>  Этот метод является оболочкой для функции Win32 `TerminateProcess` функции. Таким образом `Terminate` использует код выхода так же, как Win32 `TerminateProcess` функция использует его.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `exitCode`  
 [in] Числовое значение, — это код выхода. Допустимые числовые значения задаются в заголовке Winbase.h.  
  
## <a name="remarks"></a>Примечания  
 Если процесс остановлен `Terminate` — вызывается, процесс должен быть продолжен с помощью [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) метод, чтобы отладчик получит подтверждение о завершении через [ ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) или [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) обратного вызова.  
  
> [!NOTE]
>  Этот метод не реализуется доменом приложения. То есть оно не реализовано на <xref:System.AppDomain> уровне.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 
