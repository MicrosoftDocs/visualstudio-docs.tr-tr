---
title: Kaynak Denetimi Eklentisi API işlevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dcb07c3c49b132cdf12c1a4973af3ebf04dfa74
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796785"
---
# <a name="source-control-plug-in-api-functions"></a>Kaynak Denetimi Eklentisi API İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak Denetimi Eklentisi API kaynak denetimi eklentisi bu API uygun olarak uygulanması gereken aşağıdaki işlevleri sağlar. Her işlev ve semantiği imzalarını bit bayrakları ile ilişkili olan ve diğer parametreler, bu başvuru kaynağında ayrıntılı olarak açıklanmıştır.  
  
## <a name="initialization-and-housekeeping-functions"></a>Başlatma ve temizlik işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Bir proje kapatır.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Verilen komutu için Gelişmiş Seçenekleri kullanıcıya sorar.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Eklenti kaynak denetimi sürümünü döndürür.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Kaynak Denetimi Eklentisi başlatır. Ayrıca, eklentinin her örneği için bir kez çağrılır.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Bir proje açılır.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Çok çeşitli seçenekleri ayarlamak için kullanılan genel bir işlev. Her seçeneği ile başlayan `SCC_OPT_xxx` ve kendi tanımlanan değerleri kümesi vardır.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Kaynak Denetimi Eklentisi çekilmesine gerektiğinde sonra çağrılır.|  
  
## <a name="core-source-control-functions"></a>Çekirdek kaynak denetim işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Kaynak denetim sistemi için tam yol adları tarafından belirtilen dosya bir dizi ekler.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Kaynak denetim sistemi olan dosyalar için Gözat izin verir ve bu dosyaları bölümü geçerli projenin yapın.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Dosyaları bir dizide denetler.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Dosyaları bir dizi denetler.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Bir tam yol adı ve kaynak denetimi altında bir sürümü tarafından belirtilen yerel kullanıcı dosya arasındaki farklar gösterilmektedir.|  
|[SccGet](../extensibility/sccget-function.md)|Birtakım dosyalarda salt okunur bir kopyasını alır.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Çağıran hakkında sorular dosyaların durumunu denetler (aracılığıyla `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Kaynak denetimi eklenti için anlamlı olan bir proje yolu kullanıcıdan eklentisi neden olur.|  
|[SccHistory](../extensibility/scchistory-function.md)|Bir dizi yerel tam olarak nitelenmiş dosya adını geçmişini gösterir.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Bunların geçerli durum için dosyaların listesini inceler. Ayrıca, kullandığı `pfnPopulate` işlevi bir dosya için ölçüt eşleşmediğinde çağrıyı yapana bunu bildirmesi `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Tam olarak nitelenmiş dosya özelliklerini gösterir.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Bunların geçerli durum için tam dosyaları listesini inceler.|  
|[SccRemove](../extensibility/sccremove-function.md)|Dizinin tam dosyaların kaynak denetim sisteminden kaldırır.|  
|[SccRename](../extensibility/sccrename-function.md)|Belirtilen dosya, kaynak denetim sistemi yeni bir ad ile yeniden adlandırır.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Kaynak denetim sistemi özelliklerinin tam aralığının erişir.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Dosyaları bir dizi bir kullanıma almayı iptal eder.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Ek özelliği (kaynak denetimi eklentisi API sürüm 1.2) destekleyen işlevleri  
 Bu grubun işlevleri, kaynak denetimi eklentisi API 1.2 sürümüne dahil ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özellikleri ve yetenekleri erişim sağlar.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Bir toplu işlem başlar.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Varolan üst projesinin altında verilen ada sahip bir alt proje oluşturur.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Bir tam yol adı ve kaynak denetimi veritabanı yeri tarafından belirtilen yerel kullanıcı dizini arasındaki farklar gösterilmektedir.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Bunların geçerli durum için tam dizinler listesini inceler.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Bir toplu işlem sona erer.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Döndürür (projenin var olması gerekir) belirtilen proje yolu üst.|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Bir dosya çubuğunda birden çok kullanıma izin verilip verilmediğini denetler.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Eklenti MSSCCPRJ oluşturacak olup olmadığını denetler. SCC dosyaları.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Gelişmiş özelliği (kaynak denetimi eklentisi API sürüm 1.3) destekleyen işlevleri  
 Bu grubun işlevleri, kaynak denetimi eklentisi API 1.3 sürümüne dahil ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özellikleri ve yetenekleri erişim sağlar.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Dosyaların listesini kaynak denetiminden geçerli projeye ekler.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Bir kullanıcı arabirimi olmadan kaynak denetiminden dosyaların listesini alır.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Yerel dosyalarından farklı kaynak denetimindeki dosyalara bir listesini alır.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Kaynak Denetimi Eklentisi tarafından desteklenen genişletilmiş özellikler belirtin bayrakları alır.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Kullanıcıya özgü seçenekleri alır.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Dizinleri ve dosyaları bir proje veya kaynak denetimi altında olan projeler listesini inceler. Bulunan her dizin ve dosya adı, bir geri çağırma işlevine geçirilir.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Ad değişiklikleri için dosyaların listesini inceler. Her dosya adının, değişiklik durumu ile bir geri çağırma işlevine geçirilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: scc.h  
  
 (Ortam SDK'yı sağlanan ortak klasör, varsayılan olarak içerir *[sürücü]* \Program Files\VSIP 8.0\EnvSDK\common\inc; ayrıca VSIP klasöründe MSSCCI örnek ile sağlanan *[sürücü]* \Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)

