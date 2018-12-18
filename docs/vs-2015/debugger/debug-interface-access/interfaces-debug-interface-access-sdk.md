---
title: Arabirimler (arabirim erişimi SDK'SINDA hata ayıklama) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d74f42008a76fb9b3f5ac6966ec01721bcb32cac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809343"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yöntemleri, İçindekiler ve Vtable sırayla arabirimi sayfasındaki tabloda her arabirim alfabetik olarak listelenir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 DIA SDK'sı sanal ve göreli sanal adreslerine hata ayıklama nesneler için nasıl hesaplar üzerinde denetim sağlar.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Hata ayıklama sembolleri bir kaynak erişim başlatır.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Hata ayıklama veri akışı kayıtlara erişim sağlar.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Veri kaynağında bulunan çeşitli hata ayıklama akışları numaralandırır.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Veri kaynağında bulunan çeşitli çerçeve veri öğeleri sıralar.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Veri kaynağında bulunan çeşitli eklenen kaynakları listeleme.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Veri kaynağında bulunan çeşitli satır numaralarını numaralandırır.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Veri kaynağında bulunan çeşitli bölüm Katkıları numaralandırır.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Veri kaynağında bulunan çeşitli parçaları numaralandırır.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Veri kaynağında bulunan çeşitli kaynak dosyaları listeler.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Kullanılabilir çeşitli yığın çerçevelerini listeler.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Veri kaynağında bulunan çeşitli simgeler numaralandırır.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Veri kaynağında bulunan çeşitli simgeler adresine göre sıralar.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Veri kaynağında bulunan çeşitli tabloları sıralar.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Bir yığın çerçevesini ayrıntılarını sunar.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Modülün veya görüntü temel konum ve bellek uzaklıkları ayrıntılarını sunar.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Erişimlerinin program kaynak kodu DIA veri kaynağında depolanır.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Bir kaynak dosyası satır numarası bayt görüntü metin bloğu eşleme işlemini açıklar bilgilere erişir.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Yordamı bulmak, bu nedenle konumu denemesinin ilerleme üzerinde rapor için bir kullanıcı arabirimi etkinleştirme DIA Sembol'nden geri çağırmaları alır.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Yordam bulma, bulmayla işlemi uygulanan için kısıtlamaları izin vererek DIA Sembol'nden geri çağırmaları alır.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 DIA özellik kümesi kalıcı özelliklerini okumanıza izin verir.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Belirtilen yürütülebilir bir dosyanın dosya konumuna göre bayt sağlamak bir istemci uygulaması sağlar.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Bir göreli sanal adres tarafından belirtilen bir yürütülebilir dosyanın bayt sağlamak bir istemci uygulaması sağlar.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Bir bölüm katkı açıklayan alır verileri, diğer bir deyişle, bitişik bir bellek bloğu tarafından bir derlenecek görüntüye katkıda.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Bölüm numarası verilerden adres alanının kesimlerine eşler.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Hata ayıklama sembolleri için bir sorgu bağlamı sağlar.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Bir kaynak dosyasını temsil eder.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Yığın çerçevesinin özellikleri sunar.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 PDB dosyası kullanarak bir yığın yapmak için yöntemleri yol sağlar.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Yığın bağlamı çağrıları arasında tutar [Idiaframedata::Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yöntemi.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Program hata ayıklama veritabanı (PDB) dosyası kullanarak yığınını walking kolaylaştırır.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Sembol örneğinin özelliklerini açıklar.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 DIA veri kaynağı tablosu numaralandırır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 DIA SDK çeşitli arabirimleri tarafından kullanılan yapılar ve numaralandırmaları açıklar.  
  
 [Sabitler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 DIA SDK içinde sabitleri açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)



