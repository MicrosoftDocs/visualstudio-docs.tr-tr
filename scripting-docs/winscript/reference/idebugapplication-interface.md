---
title: Idebugapplication arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794387"
---
# <a name="idebugapplication-interface"></a>IDebugApplication Arabirimi
Uzaktan olmayan hata ayıklama yöntemlerini kullanmak için dil motorları ve ana bilgisayar tarafından gösterir.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IRemoteDebugApplication`, `IDebugApplication` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Uygulamanın adını ayarlar.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|İşlem Hata Ayıklama Yöneticisi'ni çağırıcısına hakkında bilgi döndürmek için bir dil altyapısı tek adımlı modunda olduğunu bildirir.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Hata ayıklayıcı IDE görüntülenmesine izin verilen dize neden olur.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Varsayılan hata ayıklayıcısı IDE başlatır ve değil bir zaten bağlıysa, bu uygulama için bir hata ayıklama oturumu ekler.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Engellemek geçerli iş parçacığının neden olur ve IDE hata ayıklayıcı kesme noktası bir bildirim gönderir.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Tüm başvurularını serbest bırakın ve etkin olmayan bir duruma girmek bu uygulamayı neden olur.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Uygulama için geçerli sonu bayrakları döndürür.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Şu anda çalışan iş parçacığı ile ilişkili iş parçacığı döndürür.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Belirtilen zaman uyumlu hata ayıklama işlemi zaman uyumsuz erişim sağlar.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Bir yığın çerçeve Numaralandırıcı sağlayıcısı bu uygulamaya ekler.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Yığın çerçevesi Numaralandırıcı sağlayıcı bu uygulamadan kaldırır.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Geçerli çalışan iş parçacığı hata ayıklayıcı iş parçacığı olup olmadığını belirler.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Çağıran kodu hata ayıklayıcı iş parçacığında çalıştırmak için bir mekanizma sağlar.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Belirli bir belge sağlayıcı ile ilişkili yeni bir uygulama düğümü oluşturur.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Hata Ayıklayıcı'nın için genel bir olay harekete `IApplicationDebugger` arabirimi.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Engellemek geçerli iş parçacığının neden olur ve IDE hata ayıklayıcısı hata bir bildirim gönderir.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Tam zamanında (JIT) hata ayıklayıcı kayıtlı olup olmadığını belirler.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|JIT hata ayıklayıcı otomatik-debug dumb konakları için kayıtlı olup olmadığını belirler.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Bu uygulama için bir genel ifade içerik sağlayıcı ekler.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Genel ifade içerik sağlayıcı bu uygulamadan kaldırır.|