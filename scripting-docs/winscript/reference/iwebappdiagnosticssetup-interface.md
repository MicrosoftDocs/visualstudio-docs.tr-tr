---
title: Iwebappdiagnosticssetup arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796355"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup Arabirimi
Bu arabirim ayıklanacak işlemde COM nesneleri oluşturmak ve web tanılama'yı etkinleştirmek için bir PDM hata ayıklama uygulama tarafından uygulanır. Uygulama nesnesi uygular PDM ayıklaması [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer çağırır [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) oluşturulduktan sonra ve bir başvuru geçişinde [Iwebbrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). WWA uygulama çağırır [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) ve arabirim IWebApplicationHost yerine WWA geçirir. Varsa [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) NULL olmayan bir değer ile adlı [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) true değerini döndürür. Değilse, false değerini döndürür ve çağrılar [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) başarısız.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`PDM v11.0 ve büyük uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemlerini gösterir.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Belirtilen filtre tarafından gizlenen metin belgeleri alır.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Belirtilen belge bu düğümün alt öğelerinin birine ait olup olmadığını belirler.|