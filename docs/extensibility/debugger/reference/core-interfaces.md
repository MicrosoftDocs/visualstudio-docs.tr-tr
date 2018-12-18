---
title: Çekirdek arabirimleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1eb747e15f5c8d8b02aa8a5c80f261d64044b958
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875417"
---
# <a name="core-interfaces"></a>Temel Arabirimler
Temel arabirimler kullanarak hata ayıklayıcıyı genişletmek için aşağıdaki arabirimdir [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  

## <a name="discussion"></a>Tartışma  
 Bu arabirimler, öncelikli olarak hata ayıklama altyapısı (DE) oluşturmak için kullanılır. Bunlar, kategorilere göre buraya düzenlenmiştir:  

- [Kesme Noktaları](#Breakpoints)  

- [Bağlamlar](#Contexts)  

- [Çekirdek sunucusu](#CoreServer)  

- [Hata ayıklama altyapıları](#DebugEngines)  

- [Belgeler](#Documents)  

- [Olaylar](#Events)  

- [İfadeler](#Expressions)  

- [Bellek](#Memory)  

- [Modüller](#Modules)  

- [Bağlantı Noktaları](#Ports)  

- [İşlemler](#Processes)  

- [Programlar](#Programs)  

- [Özellikler](#Properties)  

- [Yığın Çerçeveleri](#StackFrames)  

- [İş Parçacıkları](#Threads)  

- [Tür Görselleştiricileri](#TypeVisualizers)  

  Arabirim uygulayabilir varlıkları şunlardır:  

- Hata ayıklama altyapısı (DE)  

- Bağlantı noktası sağlayıcısı (PS)  

- İfade değerlendirici (EE)  

- Visual Studio (VS)  

##  <a name="Breakpoints"></a> Kesme noktaları  
 Bu arabirimler ilgili uygulama ve kesme noktaları, izleme.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|GİZLE|Bir bellek konumuna bağlı bir kesme noktasını temsil eder.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|GİZLE|Bir kesme noktası bir bellek konumuna bağlı DE gönderilir.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Bir kesme noktası istek için bir belge sağlama toplamı temsil eder.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|GİZLE|Bir bellek konumuna bağlanacak bir kesme noktası başarısız olduğunda tarafından DE gönderilir.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|GİZLE|Bir kesme noktasına ulaşıldığında tarafından DE gönderilir.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Bir kesme noktası için bir isteğini temsil eder; bekleyen kesme noktası oluşturmak için kullanılan.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Bir kesme noktası için bir isteğini temsil eder; bekleyen kesme noktası oluşturmak için kullanılan.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|GİZLE|Bir kesme noktası bağlamak için kullanılan bilgileri temsil eder.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|GİZLE|Bir bellek konumundan ilişkisiz bir kesme noktası tarafından DE gönderilir.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|GİZLE|Geçersiz bir kesme noktasını temsil eder (tarafından döndürülen `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|GİZLE|Geçersiz bir kesme noktası çözümleme bilgilerini temsil eder.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|GİZLE|Bir işlev bir kesme noktasının ayarlandığı bir konumu temsil eder.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|GİZLE|Bağlı olan bir kesme noktasını temsil eder; ilişkili bir kesme noktası oluşturmak için kullanılan.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|GİZLE|Bir numaralandırma üzerinde bağlı kesme noktaları kümesini temsil eder.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|GİZLE|Bir numaralandırma üzerinde bir bellek konumuna bağlanamadı kesme noktaları kümesinin temsil eder.|  

##  <a name="Contexts"></a> Bağlamları  
 Bu arabirimler, çeşitli bağlamları içinde hata ayıklanan programa temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|GİZLE|Bir kod yönergesi başlangıç konumunu temsil eder.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|GİZLE|Genişletir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) modülü ve işlem arabirimleri alınmasını etkinleştirmek için arabirim.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Belgede bir konumu temsil eder.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|GİZLE|Bir ifade değerlendirme bağlamı temsil eder.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|GİZLE|Bayt koleksiyonu bellekteki başlangıç konumu temsil eder.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|GİZLE|Bir yığın çerçevesi bağlamında bir kesme noktası veya özel durumu temsil eder.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|GİZLE|Bir yığın çerçevesi bağlamında bir kesme noktası veya özel durumu temsil eder.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|GİZLE|Bir numaralandırma üzerinde kod bağlamları kümesini temsil eder.|  

##  <a name="CoreServer"></a> Çekirdek sunucusu  
 Bu arabirimler, bir program ayıklanmakta olan makine temsil eder. Bunlar tarafından uygulanan [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ancak içine hata ayıklama motoru tarafından çağrılabilir.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Bilgisayar hakkında bilgilerin yanı sıra bağlantı noktaları ve bağlantı noktası sağlayıcıları erişim sağlar.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Temsil eden bir [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) uzaktan hata ayıklamayı destekler.|  

##  <a name="DebugEngines"></a> Hata ayıklama altyapıları  
 Bu arabirimler, hata ayıklama altyapısı ve ilişkili olayları temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|GİZLE|Özel hata ayıklama altyapısını temsil eder.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|GİZLE|Semboller JustMyCode ve özel durumlar yüklenmesini destekleyen bir özel hata ayıklama altyapısını temsil eder.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|GİZLE|Hata ayıklama görevlerini işlemek hazır olduğunu belirten DE her yeni örneği tarafından gönderilir.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|GİZLE|Başlatma programlar destekleyen bir özel hata ayıklama altyapısını temsil eder.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Birden çok hata ayıklama motorlarını işleyen bir program düğümünü temsil eder.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|GİZLE|SDM bir arabirimi iş parçacığı, program veya yığın çerçevesi için hata ayıklama altyapısı elde etmek bir yol sağlar.|  

##  <a name="Documents"></a> Belgeleri  
 Bu arabirimler, belgeleri (kaynak dosyaları) ve onların ilişkilendirilmiş öğelerini temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|GİZLE|Açılması için bir belge için DE tarafından gönderilir.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|GİZLE|Bir belgeden ayrıştırılmış yönergelerin akışını temsil eder.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Bir ad ve bir sınıf kimliği (CLSID) belirterek DE tarafından sağlanan bir belgeyi temsil eder.|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Hata ayıklama belge için bir sağlama toplamı temsil eder ve bileşenleri arasında sağlama toplamı geçirme sağlar.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Belirli bir deyimi ve kod içerik karşılık gelen bir belge içindeki bir konuma bir belge bağlamını temsil eder.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Bir belge içindeki genel bir konumu temsil eder.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Bir karakter uzaklığı olarak kaynak dosyada bir konumu temsil eder.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|DE tarafından sağlanan bir metin belgesi temsil eder (türetilen [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), gerçek metni belirtin.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|GİZLE|Bellekte bir kaynak dosya değişiklikleri belirlemek için DE tarafından gönderilir.|  

##  <a name="Events"></a> Olayları  
 Bu arabirimler DE oturum hata ayıklama Yöneticisi (SDM) arasında gönderilen tüm olayları temsil eder.  


| Arabirim | Uygulayan | Açıklama |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | GİZLE | Açılması için bir belge için DE tarafından gönderilir. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | GİZLE | Hata ayıklama altyapısı (DE) Bu arabirim oturum hata ayıklama Yöneticisi (SDM) durumu ayarlamak için Sembol yükleri sırasında iletisi gönderir. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | GİZLE | Bir programın sonu tamamlandığında tarafından DE gönderilir. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | GİZLE | Bir kesme noktasına bağlandığında tarafından DE gönderilir. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | GİZLE | Bağlanacak bir kesme noktası başarısız olduğunda tarafından DE gönderilir. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | GİZLE | Bir kesme noktasına ulaşıldığında tarafından DE gönderilir. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | GİZLE | İlişkisiz bir kesme noktası tarafından DE gönderilir. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | GİZLE | Belirli bir konumda durması gerektiğini olup olmadığını belirlemek için DE tarafından gönderilir. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | GİZLE | Bellekte bir kaynak dosya değişiklikleri belirlemek için DE tarafından gönderilir. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | GİZLE | Hata ayıklama görevlerini işlemek hazır olduğunu belirten DE her yeni örneği tarafından gönderilir. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | GİZLE | Hata ayıklanan programa ilk yönerge yürütmek hazır olduğunu belirten tarafından DE gönderilir. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | GİZLE | Bir hata döndürebilir, diğer olay arabirimleri tarafından okunabilir hata iletileri sağlamak için kullanılan bir arabirim. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Temel arabirim hangi tüm diğer olaydan arabirimleri türetilir. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Olaylar (belirli bir olay arabirimini uygulayan nesneler olarak ifade edilir) gönderildiği SDM tarafından uygulanan bir arabirimi temsil eder. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | GİZLE | Ayıklanan programa bir özel durum oluştu tarafından DE gönderilir. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | GİZLE | Zaman uyumsuz bir ifade değerlendirme işlemi tamamlandıktan sonra tarafından DE gönderilir. |
| IDebugFindSymbolEvent2 | | ARTIK KULLANILMIYOR. KULLANMAYIN. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | GİZLE | Ele geçirilen bir özel durum işleme tamamlandıktan sonra tarafından DE gönderilir. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | GİZLE | Bir program yüklemesi tamamlandığında tarafından DE gönderilir. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | GİZLE | IDE görüntülenmesini sağlamak için DE tarafından bir bilgi iletisidir kullanıcıya gönderilir. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | GİZLE | Bir modül yüklendiğinde veya kaldırıldı DE gönderilir. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | GİZLE | Sinyaller [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı semboller için başlatılan yürütülebilir dosya bulunamadı, kullanıcıyı uyarmak için kullanıcı Arabirimi. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | GİZLE | IDE görüntülenmesini sağlamak için DE tarafından rastgele bir dize gönderildi. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Herhangi bir dinleyici bağlantı noktası olayları iletişim kurmak için bir bağlantı noktası tarafından gönderilen. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Bir işlem oluşturulmamış DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Bir işlem kaldırıldığında DE veya bağlantı noktası tarafından gönderilen. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Bir program oluştururken DE veya bağlantı noktası tarafından gönderilen. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Bir program kaldırıldığında DE veya bağlantı noktası tarafından gönderilen. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | GİZLE | Varsayılan davranışı geçersiz kılmak bir hata ayıklama altyapısı sağlayan [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklama oturumunu sonlandırdığınızda, kullanıcı Arabirimi. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | GİZLE | Hata ayıklama altyapısı (DE) oturum hata ayıklama Yöneticisi (SDM) gönderilen bir programın adını değiştirir. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | GİZLE | Yeni bir özellik DE tarafından gönderilen (tarafından temsil edilen `IDebugProperty2` arabirimi) oluşturuldu. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | GİZLE | Bir özelliği kaldırıldığında tarafından DE gönderilir. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | GİZLE | Dönüş değeri doğru olarak gösterilecek şekilde dışı veya bir işlevin üzerinden Adımlama ile DE gönderilir. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Hata ayıklama altyapıları Ölçüm ayarlarını okumak üzere etkinleştirir uzaktan. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | GİZLE | İçinde üzerinden veya bir yönerge dışında bir adım tamamlandıktan sonra tarafından DE gönderilir. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | GİZLE | Başarılı veya başarısız bir modüle ilişkin simgeleri yükleme belirtmek için DE tarafından gönderilir. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | GİZLE | Bir iş parçacığı oluşturulduğunda tarafından DE gönderilir. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | GİZLE | Bir iş parçacığı kaldırıldığında tarafından DE gönderilir. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | GİZLE | Bir iş parçacığı adı değiştiğinde tarafından DE gönderilir. |

##  <a name="Expressions"></a> İfadeleri  
 Bu arabirimler, belirli bir bağlamda değerlendirilecek ifade temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|GİZLE|Değerlendirilecek bir ifade temsil eder. Alınan [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|GİZLE|Bir ifadenin değerlendirilme bir bağlamı temsil eder. Alınan [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabirimi.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|GİZLE|Zaman uyumsuz bir ifade değerlendirme işlemi tamamlandıktan sonra tarafından DE gönderilir.|  

##  <a name="Memory"></a> Bellek  
 Bu arabirimler, bellek bayt dizilerini temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|GİZLE|Okunan veya yazılan bellek bayt dizisini temsil eder.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|GİZLE|Bir dizinin bellekte bir konuma bayt temsil eder.|  

##  <a name="Modules"></a> Modüller  
 Bu arabirimleri temsil eden bir yürütülebilir dosyaya karşılık gelen bir modül veya. DLL dosyası.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|GİZLE|Tek bir yürütülebilir dosya veya DLL temsil eder.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|GİZLE|Temsil eden bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , simgeleri destekler.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|GİZLE|Bir modül yüklendiğinde veya kaldırıldı DE gönderilir.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|GİZLE|PDB dosyasında yer alan kaynak sunucu bilgileri temsil eder.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|GİZLE|Bir numaralandırma tarafından bilinen modülleri kümesi üzerinden temsil eder bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  

##  <a name="Ports"></a> Bağlantı noktaları  
 Bu arabirimler, bağlantı noktası ve bağlantı noktası sağlayıcıları temsil eder.  


| Arabirim | Uygulayan | Açıklama |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Yerel bilgisayardaki varsayılan bağlantı noktasını temsil eder. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Sorun için DCOM kullanan bir hata ayıklama altyapısı sağlar [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] güvenlik duvarı uzaktan hata ayıklama engellemez emin olmak için kullanıcı Arabirimi. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Bir bağlantı noktasını temsil eder. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Herhangi bir dinleyici bağlantı noktası olayları iletişim kurmak için bir bağlantı noktası tarafından gönderilen. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Başlatma ve sonlandırma işlemleri bir bağlantı noktasını temsil eder. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Kaydolun ve bir bağlantı noktası programlarla kaydını silmek için kullanılır. şu anda hataları ayıklanan programları izlemek bağlantı noktası sağlar. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Özelleştirilmiş bir kullanıcı Arabirimi, bağlantı noktası seçmek için temsil eder. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | İçinden yeni bir bağlantı noktası oluşturulacak bulunan veya bir bağlantı noktası için bir isteğini temsil eder. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Bağlantı noktalarının bir tedarikçi temsil eder. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Kalıcı bağlantı noktalarının bir tedarikçi temsil eder (diske kaydet) bilgilerini oluşturulduğu bağlantı noktaları. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Sağlar [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] içindeki metni görüntülemek için kullanıcı Arabirimi **aktarım bilgi** bölümünü **iliştirme** iletişim kutusu. |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Hedef bilgisayar hakkında bilgi için sorgulama sağlar. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Bir numaralandırma, bir dizi bağlantı noktası temsil eder. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Bir numaralandırma üzerinde bağlantı noktası sağlayıcıları kümesini temsil eder. |

##  <a name="Processes"></a> İşlemler  
 Bu arabirimler, işlemler, bir veya daha fazla programları içeren tek bir yürütülebilir dosyayı temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Bir bilgisayar üzerinde çalışan bir işlemi temsil eder.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Etkin bir şekilde destekleyen bir işlemi temsil eden hata ayıklama (adım değiştirmek için kullanılan, devam etmek ve üzerinde bir yöntem yürütülemez [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Bir işlem oluşturulmamış DE veya bağlantı noktası tarafından gönderilir.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Bir işlem kaldırıldığında DE veya bağlantı noktası tarafından gönderilen.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Oturum bağlı izleyen bir işlemi temsil eder.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Numaralandırması bir bağlantı noktası üzerinde işlemler kümesini temsil eder.|  

##  <a name="Programs"></a> Programlar  
 Bu arabirimler, programları yürütme mutlaka bir fiziksel yürütülebilir veya modül benzemez mantıksal birimleri temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|GİZLE|Temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , aynı anda hataları ayıklanan diğer programları ile birlikte çalışması gerekir.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Bir mantıksal birim yürütme temsil eder.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Bir program oluştururken DE veya bağlantı noktası tarafından gönderilen.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Bir program kaldırıldığında DE veya bağlantı noktası tarafından gönderilen.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Temsil eden bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) birden çok hata ayıklama motoru tarafından işlenebilir.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) getirilmesi gereken oturum bağlı izleyebilirsiniz.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , içinde çalıştığı işlemi hakkındaki bilgileri döndürebilir.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Hata ayıklaması yapılabilir bir program temsil eder.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Bir programı ilişkili programa ekleme girişimi bildirilmesini düğüme sağlar.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|GİZLE|SDM bir DE bu DE tarafından denetlenen programlar hakkında sorgulamak bir yol sağlar.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Programları ayıklanmakta göstermek için ilgili SDM kaydetmek için DEs tarafından kullanılır.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Temsil eden bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , sıralama arabirimleri iş parçacığı veya işlem sınırları boyunca.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Bir dizi program numaralandırması temsil eder.|  

##  <a name="Properties"></a> Özellikleri  
 Bu arabirimler, özellikleri, genellikle bir ifade değerlendirme sonucu gibi belirli bir bağlam ile ilişkili bir değeri temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , görüntüleyebilir, değeri özel bir biçimde.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|GİZLE|Bir yığın çerçevesi, belge veya bir ifade değerlendirme sonucu bir değeri temsil eder.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|GİZLE|Temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , rasgele uzun dizeler destekler.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|GİZLE|Yeni bir özellik DE tarafından gönderilen (tarafından temsil edilen [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi) oluşturuldu.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|GİZLE|Bir özelliği kaldırıldığında tarafından DE gönderilir.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|GİZLE|Herhangi belirli bir yığın çerçevesi dışında bulunabilir bir özelliğe başvuruyu temsil eder.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|GİZLE|Bir numaralandırma üzerinde kümesini temsil eder [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılar değişkenleri, kayıtları, parametreleri ve ifadeler açıklanmaktadır.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|GİZLE|Bir numaralandırma üzerinde kümesini temsil eder [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapıları.|  

##  <a name="StackFrames"></a> Yığın çerçeveleri  
 Bu arabirimleri temsil eden bir yığın çerçevesi bir bağlam içinde bir kesme noktası veya özel durum oluştu.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|GİZLE|Bir bağlamı temsil eder, bir kesme noktası veya özel durum oluştu.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|GİZLE|Temsil eden bir [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , işleyebileceği özel durum kesildi.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|GİZLE|Bir numaralandırma üzerinde kümesini temsil eder [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) belirttiğiniz işlev yapıların belirli bir yığın çerçevesini ulaşmak için kullanılan dizisi çağırın.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|GİZLE|Bir numaralandırma üzerinde kümesini temsil eder [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yığın çerçevelerini açıklayan yapılar.|  

##  <a name="Threads"></a> İş parçacıkları  
 Bu arabirimler, iş parçacıkları ve ilişkili olayları temsil eder.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|GİZLE|Yürütme iş parçacığı temsil eder.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|GİZLE|Bir iş parçacığı oluşturulduğunda tarafından DE gönderilir.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|GİZLE|Bir iş parçacığı kaldırıldığında tarafından DE gönderilir.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|GİZLE|Bir iş parçacığı adı değiştiğinde tarafından DE gönderilir.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|GİZLE|Bir numaralandırma üzerinde iş parçacıkları kümesini temsil eder.|  

##  <a name="TypeVisualizers"></a> Tür Görselleştiricileri  
 Bu arabirimler tür görselleştiricileri için destek sağlar. Bu arabirimler genellikle bir ifade değerlendiricisi tarafından uygulanır.  

|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Bir tür görselleştiricisi için sunulacak bayt dizisini temsil eder.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Bir tür görselleştiricisi için geçirilecek verilere erişim almak için yöntemler sağlar.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Erişim sağlayan bir özellik temsil eden [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) uygulamaları.|  

## <a name="see-also"></a>Ayrıca Bkz.  
 [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../../extensibility/debugger/creating-a-custom-debug-engine.md)