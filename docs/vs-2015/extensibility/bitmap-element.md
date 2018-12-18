---
title: Bitmap öğesi | Microsoft Docs
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
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbeb175c8e4f9902fafbfdb8df4f5d83387980a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789947"
---
# <a name="bitmap-element"></a>Bitmap Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir bit eşlem tanımlar. Bit eşlemin bir kaynaktan veya bir dosya yüklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|GUID|Gerekli. GUID/ID komut tanımlayıcısı GUİD'si.<br /><br /> Guid özniteliği bir bit eşlem için herhangi bir VSPackage veya diğer komut grubuyla ilişkili değil.  Bit eşlem tanımına benzersiz olması ve başka bir amaçla kullanılmamalıdır.|  
|resID|Kimliği bir GUID/ID komut tanımlayıcısı. ResID veya href özniteliği gereklidir.<br /><br /> ResID özniteliği birleştirme komut tablosu sırasında yüklenecek olan bit eşlem Şerit belirleyen bir tamsayı kaynak kimliğidir.  Komut tablosu yüklenirken, kaynak kimliği tarafından belirtilen bit eşlemleri aynı modülünü kaynaktan yüklenir.|  
|usedList|ResID özniteliği mevcut ise gereklidir. Kullanılabilir görüntüler, bit eşlem şeridinde seçer.|  
|href|Bit eşlem yolu. ResID veya href özniteliği gereklidir.<br /><br /> Sonuçta elde edilen ikili dosyada gömülü belirtilen görüntü dosyasının yoluna aranır.  Komut tablosu birleştirme sırasında görüntünün kopyalanır ve ek kaynak araması ya da yük gereklidir.  Şerit'ndaki tüm görüntüler usedList öznitelik mevcut değilse kullanılabilir. **Not:** görüntüleri .bmp, .png ve. gif'i kapsar biçimlerden birinde sağlanabilir.  Önceki derleyici sürümleri için kısmi saydam alfa bilgilerine sahip 32-bit bit eşlem resimleri desteklememektedir. Geçici çözüm bu sürümleri için .png biçimi kullanmaktır.|  
|Koşul|İsteğe bağlı. Bkz: [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Bitmaps Öğesi](../extensibility/bitmaps-element.md)|Bit eşlem öğeleri gruplandırır.|  
  
## <a name="example"></a>Örnek  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

