---
title: CompilandDetails | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b1288a3bde1a8d17f40971744298adb1e1ecffb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468814"
---
# <a name="compilanddetails"></a>CompilandDetails
Derlenecek dosya bilgileri sembolleriyle arasında bölünür bir `SymTagCompiland` etiketi (düşük ayrıntı) ve bir `SymTagCompilandDetails` etiketi (yüksek ayrıntı). `SymTagCompilandDetails` Ek simgeleri yüklenmesini gerektirir. Ancak, çok sayıda ile kullanılamıyor derlenecek hakkında bilgi sağlayan bir `SymTagCompiland` simgesi.  
  
## <a name="properties"></a>Özellikler  
 Aşağıdaki tabloda bu simge türü için geçerli olan özellikleri gösterir.  
  
|Özellik|Veri türü|Açıklama|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Arka uç yapı derleyici sayısı.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Derleyici arka uç ana sürüm numarası.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Derleyici arka uç ikincil sürüm numarası.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|(Yalnızca DIA SDK V8.0 veya sonrası) bu derlenecek üretilen derleyici adı.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Düzenle ve devam et derleme etkinleştirilmişse.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Ön uç yapılandırma derleyici sayısı.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Derleyici ön uç ana sürüm numarası.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Derleyici ön uç alt sürüm numarasını.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Bu derlenecek hata ayıklama bilgileri (yalnızca DIA SDK V8.0 veya sonrası) varsa.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Bu derlenecek (yalnızca DIA SDK v8.0 veya sonrası) yönetilen kodu içeriyorsa.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` derlenecek dosya ile derlenen varsa [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check) derleyici anahtarı (yalnızca DIA SDK V8.0 veya üzeri).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` derlenecek dosya ortak Ara dili (CIL) koddan yerel koda dönüştürüldü durumunda.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Kullanıcı tanımlı türler (UDT) için hizalı durumunda bazı bellek sınırı (yalnızca DIA SDK V8.0 veya sonrası) belirttiniz.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` derlenecek dosya ile derlenen varsa [/hotpatch (düzeltme eki eklenebilen görüntü oluşturma)](/cpp/build/reference/hotpatch-create-hotpatchable-image) derleyici anahtarı (yalnızca DIA SDK v8.0 veya üzeri).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` derlenecek dosya ile derlenen varsa [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation) derleyici anahtarı (yalnızca DIA SDK V8.0 veya üzeri).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Derlenecek dosya Microsoft Ara dili (MSIL) Modülü (yalnızca DIA SDK v8.0 veya sonrası) ise TRUE.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Kaynak kodu dili.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Derlenecek dosya simgesi.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simge kimliği.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Derlenecek derlenmiş üzerinde platform (birini [CV_CPU_TYPE_e numaralandırması](../../debugger/debug-interface-access/cv-cpu-type-e.md) değerleri).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Dizin kimliği simgesi.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagCompilandDetails` (birini [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) değerleri).|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyicileri genellikle iki geçişi derleyici bilinen bir form gelir; bazı derleyici sürümler her geçişte ayrı bir program tarafından ele alınır. Bu ön uç ve arka uç derleyicileri sırasıyla, bu nedenle arka uç ve ön uç sürüm numaraları için Sembol Özellikleri denir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlenecek dosya](../../debugger/debug-interface-access/compiland.md)   
 [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)