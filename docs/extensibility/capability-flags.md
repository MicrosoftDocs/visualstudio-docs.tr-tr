---
title: Özellik bayrakları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36fa879ac08f81ffd61cb8febf4183ec268d3a6c
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231066"
---
# <a name="capability-flags"></a>Özellik bayrakları
SCC_CAP_*xxx* bayraklar: kaynak denetimi eklentisi yeteneklerini belirtmek için kullanılan bit bayrakları. SCC_EXCAP_*xxx* bayraklar genişletilmiş özellikler belirtin ve tam sayı değerlerine çözmek artımlı bayrakları.  
  
|Özellik kod|Değer|Açıklama|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Destekler [SccRemove](../extensibility/sccremove-function.md) ve komutu.|  
|`SCC_CAP_RENAME`|0x00000002L|Destekler [SccRename](../extensibility/sccrename-function.md) ve komutu.|  
|`SCC_CAP_DIFF`|0x00000004L|Destekler [SccDiff](../extensibility/sccdiff-function.md) ve komutu.|  
|`SCC_CAP_HISTORY`|0x00000008L|Destekler [SccHistory](../extensibility/scchistory-function.md) ve komutu.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Destekler [SccProperties](../extensibility/sccproperties-function.md) ve komutu.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Destekler [SccRunScc](../extensibility/sccrunscc-function.md) ve komutu.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Destekler [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) ve komutu.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Destekler [Sccqueryınfo](../extensibility/sccqueryinfo-function.md) ve komutu.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Destekler [SccGetEvents](../extensibility/sccgetevents-function.md) ve komutu.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Destekler [SccGetProjPath](../extensibility/sccgetprojpath-function.md) ve komutu.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Destekler [SccAddFromScc](../extensibility/sccaddfromscc-function.md) ve komutu.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Bir açıklama üzerinde kullanıma almayı destekler.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Bir yorum, iade etme üzerinde destekler.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Yorum Ekle destekler.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Bir açıklamayı Kaldır destekler.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|IDE tarafından sağlanan çıkış işlevi için metin yazar.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Deltaları içermeyen dosyaları depolamak destekler.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Birden çok dosya geçmişi destekler.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Büyük küçük harf duyarsız dosya karşılaştırma destekler.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Beyaz boşluğu yok sayar karşılaştırma dosya destekler.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Ek dosyaları üretmeyi destekler.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Destekler açıklamaları projesi oluşturun.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Fark tüm durumlarda ise denetimindeki destekler.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Eklenti bir kullanıcı Arabirimi için Get desteklemez, ancak IDE hala çağırıp [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Eklenti desteklemeyeceğini ve iş parçacığı açısından güvenli değildir. Sürüm 1.0, hiçbir eklenti desteklemeyeceğini ve iş parçacığı güvenli olarak kabul edildiği. Bir eklenti 1.1 bitini, konak paralel olarak birden çok proje açmak için izin verilir.|  
  
## <a name="capability-bits-added-in-version-12"></a>Özellik BITS sürüm 1.2 eklendi  
  
|Özellik kod|Değer|Açıklama|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Destekler [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Destekler [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Destekler [SccBeginBatch](../extensibility/sccbeginbatch-function.md) ve [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Destekler [Sccdirqueryınfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Destekler [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Bir dosyayı birden çok kullanıma destekler ve [Sccısmulticheckoutenabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Destekler *MSSCCPRJ.SCC* dosyası (kullanıcı/yönetici geçersiz kılma) tabi ve [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Özellik BITS sürüm 1.3 eklendi  
 Bu bayrak için teker teker geçirilir [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) yeteneği desteklenip desteklenmediğini belirlemek için işlevi.  
  
|Genişletilmiş özellik kod|Değer|Açıklama|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1.|Destekler `SCC_CHECKOUT_LOCALVER` kullanıma alma seçeneği.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Destekler [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Destekler [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Ek dizinleri üretmeyi destekler.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Dosya değişiklikleri numaralandırma destekler.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Destekler [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Destekler [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Birden çok iş parçacığında Sccqueryınfo çağrılmasını destekler.|  
|`SCC_EXCAP_REMOVE_DIR`|9|SccRemoveDir işlevi destekler.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Kullanıma dosyaları silebilirsiniz.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Kullanıma dosyaları yeniden adlandırabilirsiniz.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)