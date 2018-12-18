---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796337"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Bu yöntem kimliği ile geçirdiğiniz sınıfı birlikte oluşturur `rclsid` kullanarak `dwClsContext`. Benzer şekilde budur [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) durumunda hariç works `CreateObjectWithSiteAtWebApp` nesne zaman uyumsuz olarak web uygulamasının UI iş parçacığında oluşturuldu. Sınıf kimliği tarafından belirtilen nesne uygulamalıdır [Iwebappdiagnosticsobjectınitialization arabirimi](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Nesne oluşturulduktan sonra [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) PDM hata ayıklama uygulama başvuru olarak adlandırılır ve `hPassToObject` parametresinin `CreateObjectWithSiteAtWebApp`. Uygulamaya bir tanıtıcı kullanarak kopyaladığınız anonim bir kanala geçirmek için bu yöntemi kullanabilirsiniz [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [Iwebappdiagnosticssetup arabirimi](../../winscript/reference/iwebappdiagnosticssetup-interface.md) PDM v11.0 tarafından uygulanan ve büyük. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `rclsid`  
 Sınıf kimliği oluşturma sınıf.  
  
 `dwClsContext`  
 Kod çalışacağı bağlamı. Çoğu durumda bu CLSCTX_INPROC_SERVER olur.  
  
 `riid`  
 Kullanılmadı.  
  
 `hPassToObject`  
 Kullanıcı Arabirimi iş parçacığı üzerinde oluşturulduğunda nesne uyguluyorsa nesnesine geçirilen bir değer [Iwebappdiagnosticsobjectınitialization arabirimi](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).