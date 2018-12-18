---
title: Kaynak Denetim eklentisi API işlevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a834c4352ea2444c2669a57f760ed373999b07dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144375"
---
# <a name="source-control-plug-in-api-functions"></a>Kaynak Denetim eklentisi API işlevleri
Kaynak Denetim eklentisi API uygun olarak bu API eklentisinin kaynak denetimi tarafından uygulanan gerekir aşağıdaki işlevleri sağlar. Her işlev ve semantiğini imzalarını bit bayrakları ile ilişkili olan ve diğer parametreleri bu başvuru kaynağında ayrıntılı olarak açıklanmıştır.  
  
## <a name="initialization-and-housekeeping-functions"></a>Başlatma ve temizlik işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Bir proje kapatır.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Verilen komut için Gelişmiş Seçenekleri kullanıcıya sorar.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Kaynak denetimi sürümünü eklenti döndürür.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Kaynak Denetim eklentisi başlatır. Ayrıca, her örneği eklenti için bir kez çağrılır.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Bir proje açar.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Çok çeşitli seçenekleri ayarlamak için kullanılan genel bir işlev. Her seçeneği ile başlayan `SCC_OPT_xxx` ve kendi tanımlanan değerleri kümesi vardır.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Kaynak Denetim eklentisi takılı olması gerektiği zaman bir kez çağrılır.|  
  
## <a name="core-source-control-functions"></a>Çekirdek kaynak denetim işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Kaynak denetim sistemi için tam yol adları tarafından belirtilen dosya bir dizi ekler.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Kaynak denetimi sistemde zaten olan dosyaları göz atmak kullanıcının sağlar ve bu dosyaları bölümü geçerli projenin yapın.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Dosyaları bir dizi denetler.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Dosyaları bir dizi denetler.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Bir tam yol adı ve sürümü kaynak denetimi altında tarafından belirtilen yerel kullanıcı dosya arasındaki farklılıkları gösterir.|  
|[SccGet](../extensibility/sccget-function.md)|Birtakım dosyalarda salt okunur bir kopyasını alır.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Çağıran hakkında istedi dosyaların durumunu denetler (aracılığıyla `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Kaynak Denetim eklenti için anlamlı bir proje yol kullanıcıdan eklentisi neden olur.|  
|[SccHistory](../extensibility/scchistory-function.md)|Tam yerel dosya adlarının dizisini geçmişini gösterir.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Bunların geçerli durum için dosyaları listesi inceler. Ayrıca, kullanır `pfnPopulate` işlevi çağıran bir dosya için ölçüt eşleşmediğinde bildirmek için `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Bir tam dosya özelliklerini gösterir.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Bunların geçerli durum için tam dosyaların listesini inceler.|  
|[SccRemove](../extensibility/sccremove-function.md)|Tam dosyaları dizisi kaynak denetimi sisteminden kaldırır.|  
|[SccRename](../extensibility/sccrename-function.md)|Verilen dosya için yeni bir ad kaynak denetim sistemi yeniden adlandırır.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Kaynak denetim sistemi özelliklerini tam aralığını erişir.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Dosyaların bir dizinin bir checkout geri alır.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Ek özelliği (sürüm 1.2 kaynak denetimi eklenti API) destekleyen işlevleri  
 Bu grubun işlevleri kaynak denetim eklentisi API 1.2 sürümüne dahil ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özellikleri ve yetenekleri erişim sağlar.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Bir toplu işlemi başlatır.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Varolan üst projesini altında verilen ada sahip bir alt oluşturur.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Bir tam yol adı ve kaynak denetim veritabanı konumu tarafından belirtilen yerel kullanıcı dizini arasındaki farklar gösterilmektedir.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Bunların geçerli durum için tam dizinler listesinde inceler.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Bir toplu işlemi sonlandırır.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Döndürür (proje var olmalıdır) verilen proje yolunu üst.|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Dosyada birden çok kullanıma izin verilip verilmediğini denetler.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Eklenti MSSCCPRJ oluşturacak olup olmadığını denetler. SCC dosyalar.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Gelişmiş özelliği (1.3 kaynak denetimi eklenti API sürümü) destekleyen işlevleri  
 Bu grubun işlevleri kaynak denetim eklentisi API 1.3 sürümüne dahil ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özellikleri ve yetenekleri erişim sağlar.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Dosyaların listesini kaynak denetiminden geçerli projeye ekler.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Kullanıcı arabirimi olmadan kaynak denetiminden dosyaların bir listesini alır.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Kaynak denetiminde yerel dosyalarından farklı dosyaların bir listesini alır.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Kaynak Denetimi Eklentisi tarafından desteklenen genişletilmiş özellikleri belirtin bayraklarını alır.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Kullanıcıya özgü seçeneklerini alır.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Dizinler ve dosyalar bir proje veya kaynak denetimi altında olan projeler listesini inceler. Bulunan her dizin ve dosya adı için bir geri çağırma işlevini geçirilir.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Dosyaların listesi için ad değişikliklerinin inceler. Her dosya adı, değişiklik durumu ile bir geri çağırma işlevini geçirilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: scc.h  
  
 (Ortamı SDK'ın sağlanan ortak klasörü, varsayılan olarak, içerir *[sürücü]* \Program Files\VSIP 8.0\EnvSDK\common\inc; ayrıca MSSCCI örnekle VSIP klasöründe sağlanan *[sürücü]* \Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetim Eklentileri](../extensibility/source-control-plug-ins.md)   
 [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)