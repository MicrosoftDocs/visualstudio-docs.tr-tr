---
title: Biçimlendirme, XML, metin düzenleyici, Seçenekler iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c8379393dd5327359789f8621cf67ed55e89209
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256678"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Biçimlendirme, XML, Metin Düzenleyici, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu iletişim kutusu, XML Düzenleyicisi için biçimlendirme ayarları belirtmenize olanak sağlar. Erişebildiğiniz **seçenekleri** iletişim kutusundan **Araçları** menüsü.  
  
> [!NOTE]
>  Seçtiğinizde, bu ayarlar kullanılabilir **metin düzenleyici** klasöründe **XML** klasörünü ve ardından **biçimlendirme** seçeneğini **seçenekleri** iletişim kutusu.  
  
## <a name="attributes"></a>Öznitelikler  
 **El ile öznitelik biçimlendirmeyi koru**  
 Öznitelikleri getirilecek değil. Bu varsayılandır.  
  
> [!NOTE]
>  Öznitelikler üzerinde birden fazla satır varsa, düzenleyici üst öğenin girintisini eşleştirilecek özniteliklerin her satırı girintiler.  
  
 **Öznitelikleri her biri kendi satırında Hizala**  
 Dikey olarak ilk öznitelik girintisini eşleştirmek için ikinci ve sonraki öznitelikleri hizalar. Aşağıdaki XML nasıl öznitelikleri hizalanmış bir örnek metindir.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## <a name="auto-reformat"></a>Otomatik yeniden Biçimlendir  
 **Panodan yapıştırma**  
 XML metni panodan yapıştırılan yeniden biçimlendirir.  
  
 **Bitiş etiketi tamamlandığında**  
 Öğe bitiş etiketi tamamlandığında yeniden biçimlendirir.  
  
## <a name="mixed-content"></a>Karışık içerik  
 **Varsayılan olarak karışık içeriği korumak**  
 Düzenleyici karışık içerik yeniden biçimlendirir olup olmadığını belirler. Varsayılan olarak, düzenleyici içeriği ne zaman bulunur dışında karışık içeriği yeniden biçimlendirmek çalışır. bir `xml:space="preserve"` kapsam.  
  
 Bir öğe metni ve biçimlendirmeyi bir karışımını içeriyorsa, içeriği içerik karışık kabul edilir. Karışık içerikli bir öğenin bir örnek verilmiştir.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge özellikleri, özellik penceresi](../xml-tools/xml-document-properties-properties-window.md)   
 [XML Düzenleyicisi Bileşenleri](../xml-tools/xml-editor-components.md)



