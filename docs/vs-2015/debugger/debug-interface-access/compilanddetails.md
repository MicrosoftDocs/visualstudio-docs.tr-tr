---
title: CompilandDetails | Microsoft Docs
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
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e94993440a8fba4b215cb7a7b32f55f98475fb51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769070"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Derlenecek bilgi simgeleri ile arasında bölünür bir `SymTagCompiland` etiketi (az ayrıntı) ve bir `SymTagCompilandDetails` etiketi (yüksek ayrıntı). `SymTagCompilandDetails` Ek sembol yüklenmesi gerekir. Ancak, çok sayıda kullanıma hazır değil derlenecek hakkında bilgi sağlar. bir `SymTagCompiland` sembol.  
  
## <a name="properties"></a>Özellikler  
 Aşağıdaki tabloda bu sembol türü için geçerli olan özellikleri gösterir.  
  
|Özellik|Veri türü|Açıklama|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Derleyicinin arka uç yapı numarası.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Derleyicinin arka uç ana sürüm numarası.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Derleyicinin arka uç alt sürüm numarası.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|(Yalnızca DIA SDK V8.0 veya üzeri sürümlerde) bu derlenecek üretilen derleme adı.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` derleme için Düzenle ve devam et etkinleştirildiyse.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Derleyici ön derleme sayısı.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Derleyici ön uç ana sürüm sayısı.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Derleyici ön uç alt sürüm sayısı.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Bu derlenecek hata ayıklama bilgileri (yalnızca DIA SDK V8.0 veya üzeri) sahipse.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Bu derlenecek (yalnızca DIA SDK v8.0 veya üzeri sürümlerde) yönetilen kodu içeriyorsa.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` derlenecek ile derlenen varsa [/GS (arabellek güvenlik denetimi)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) derleyici anahtarı (yalnızca DIA SDK V8.0 veya üzeri).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` derlenecek ortak Ara dil (CIL) koddan yerel koda dönüştürülmüş durumunda.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Kullanıcı tanımlı tür (UDT) için hizalı durumunda bazı bellek sınırı (yalnızca DIA SDK V8.0 veya üzeri) belirttiniz.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` derlenecek ile derlenen varsa [/hotpatch (düzeltme eki eklenebilen görüntü oluşturma)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) derleyici anahtarı (yalnızca DIA SDK v8.0 veya üzeri).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` derlenecek ile derlenen varsa [/LTCG (bağlama zamanı kodu oluşturma)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) derleyici anahtarı (yalnızca DIA SDK V8.0 veya üzeri).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Derlenecek bir Microsoft Ara dil (MSIL) modülünün (yalnızca DIA SDK v8.0 veya üzeri sürümlerde) ise TRUE.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Kaynak kod dili.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Derlenecek dosya simgesi.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simge kimliği.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Derlenecek derlendiği platform (biri [CV_CPU_TYPE_e numaralandırması](../../debugger/debug-interface-access/cv-cpu-type-e.md) değerler).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembol, dizin kimliği.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagCompilandDetails` (biri [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) değerler).|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyiciler genellikle iki geçişli derleyici bilinen bir formda gelir; bazı derleyici sürümlerinde, her geçişi ayrı bir program tarafından ele alınır. Bu ön uç ve arka uç derleyicileri, sırasıyla, bu nedenle arka ve ön uç sürüm numaraları için Sembol Özellikleri bilinir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlenecek](../../debugger/debug-interface-access/compiland.md)   
 [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



