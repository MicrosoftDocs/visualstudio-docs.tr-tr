---
title: SymTagEnum | Microsoft Docs
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
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09462ee9d9223c79b4ee0dcf4e8a5efa37b4c796
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783317"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Simgenin türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Öğeleri  
 `SymTagNull`  
 Simgenin türü yok sahip olduğunu gösterir.  
  
 `SymTagExe`  
 Simgenin bir .exe dosyası olduğunu gösterir. Yalnızca bir tane `SymTagExe` sembolü sembol deposu başına. Genel kapsam görev yapar ve sözcük temelli bir üst öğesi yok.  
  
 `SymTagCompiland`  
 Sembol deposundaki her derlenecek bileşeni derlenecek dosya simgesi gösterir. Yerel uygulamalar için `SymTagCompiland` sembolleri görüntüye bağlı nesne dosyaları karşılık gelir. Microsoft Ara dil (MSIL) görüntüleri bazı tür için bir derlenecek sınıfı başına yoktur.  
  
 `SymTagCompilandDetails`  
 Simgenin derlenecek genişletilmiş öznitelikleri içerdiğini gösterir. Bu özellikleri alınırken derlenecek semboller yükleniyor gerektirebilir.  
  
 `SymTagCompilandEnv`  
 Simgenin derlenecek için tanımlı bir ortam dize olduğunu gösterir.  
  
 `SymTagFunction`  
 Simgenin bir işlevi olduğunu gösterir.  
  
 `SymTagBlock`  
 Simgenin iç içe geçmiş bir bloğu gösterir.  
  
 `SymTagData`  
 Simgenin veri olduğunu gösterir.  
  
 `SymTagAnnotation`  
 Simgenin bir kod ek açıklamaları için olduğunu gösterir. Bu simge, alt sabit veri dizelerdir (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Çoğu istemci, bu simgeyi yoksayın.  
  
 `SymTagLabel`  
 Simge bir etiket olduğunu gösterir.  
  
 `SymTagPublicSymbol`  
 Simgenin bir ortak sembol olduğunu gösterir. Yerel uygulamalar için bu görüntünün bağlarken karşılaştı COFF dış sembol semboldür.  
  
 `SymTagUDT`  
 Simgenin bir kullanıcı tanımlı türü (yapısı, sınıf veya birleşim) olduğunu gösterir.  
  
 `SymTagEnum`  
 Simgenin bir numaralandırma olduğunu gösterir.  
  
 `SymTagFunctionType`  
 Simgenin bir işlev imzası türü olduğunu gösterir.  
  
 `SymTagPointerType`  
 Simgenin bir işaretçi türü olduğunu gösterir.  
  
 `SymTagArrayType`  
 Simgenin bir dizi türü olduğunu gösterir.  
  
 `SymTagBaseType`  
 Simgenin bir taban türü olduğunu gösterir.  
  
 `SymTagTypedef`  
 Sembol olduğunu belirten bir `typedef`, diğer bir deyişle, başka bir tür diğer adı.  
  
 `SymTagBaseClass`  
 Simgenin bir temel sınıf bir kullanıcı tanımlı tür olduğunu gösterir.  
  
 `SymTagFriend`  
 Simgenin bir arkadaş bir kullanıcı tanımlı tür olduğunu gösterir.  
  
 `SymTagFunctionArgType`  
 Simgenin bir işlev bağımsız değişkeni olduğunu gösterir.  
  
 `SymTagFuncDebugStart`  
 Simgenin işlevin prolog kodunu bitiş konumunun olduğunu gösterir.  
  
 `SymTagFuncDebugEnd`  
 Simgenin işlevin Epilog kodu başlangıç konumunu gösterir.  
  
 `SymTagUsingNamespace`  
 Simgenin bir ad alanı adı, geçerli kapsamda etkin olduğunu gösterir.  
  
 `SymTagVTableShape`  
 Simgenin sanal tablo açıklamasını belirtir.  
  
 `SymTagVTable`  
 Simgenin bir sanal tablosu işaretçisi olduğunu gösterir.  
  
 `SymTagCustom`  
 Simgenin özel bir simge ve DIA. tarafından yorumlanır değil gösterir  
  
 `SymTagThunk`  
 Simgenin 16 ve 32 bit kod arasında veri paylaşımı için kullanılan bir dönüştürücü olduğunu gösterir.  
  
 `SymTagCustomType`  
 Simgenin bir özel derleyici sembol olduğunu gösterir.  
  
 `SymTagManagedType`  
 Sembol meta verilerde olduğunu gösterir.  
  
 `SymTagDimension`  
 Simgenin FORTRAN çok boyutlu bir dizi olduğunu gösterir.  
  
 `SymTagCallSite`  
 Simgenin çağrı sitesini temsil ettiğini gösterir.  
  
 `SymTagInlineSite`  
 Simgenin satır içi siteyi temsil ettiğini gösterir.  
  
 `SymTagBaseInterface`  
 Simgenin bir taban arabirimi olduğunu gösterir.  
  
 `SymTagVectorType`  
 Simgenin bir vektör türü olduğunu gösterir.  
  
 `SymTagMatrixType`  
 Simgenin bir matris türü olduğunu gösterir.  
  
 `SymTagHLSLType`  
 Simgenin yüksek düzey gölgelendirici dili türü olduğunu gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama dosya içindeki tüm sembolleri simgenin türünü belirten bir tanımlama etiketi vardır.  
  
 Bu numaralandırma değerleri için yapılan bir çağrı tarafından döndürülen [Idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) yöntemi.  
  
 Bu sabit listesi değerleri, belirli sembol türü için arama kapsamını sınırlandırmak için aşağıdaki yöntemleri için geçirilir:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: cvconst.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri ve yapıları](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Simge türlerinin sözcük hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Idiasession::findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Idiasession::findsymbolbyrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Idiasession::findsymbolbyrvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Idiasession::findsymbolbytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Idiasession::findsymbolbyva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Idiasession::findsymbolbyvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)



