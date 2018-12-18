---
title: XML belge özellikleri, Özellikler penceresinde | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c93defe6f5c56966195f1514b5aa76464f6f3013
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236567"
---
# <a name="xml-document-properties-properties-window"></a>XML Belge Özellikleri, Özellik Penceresi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
**Özellikleri** penceresi XML Düzenleyicisi'nde etkin belgeyi hakkında temel bilgiler sağlar. Kullanılabilir özellikler şu anda etkin olan bir XML belgesi türüne bağlı olarak değişir.  
  
> [!NOTE]
>  Çözümdeki tüm XML belge özellikleri kaydedilir. Sonuç olarak, çözüm bir sonraki açışınızda bu değerleri girmek gerekmez.  
  
 **Kodlama**  
 Dosya için kodlama karakter. Bu özellik değişiklikleri kodlama özniteliği XML bildirimi ve tam tersi de değiştiriliyor. Yeni kodlama dosyasını kaydettiğinizde dosyanın kodlamak için kullanılır.  
  
 **Giriş**  
 XSLT stil sayfası ile ilişkili giriş belgesi. Tarafından kullanılan **ShowXSLT çıkış** komutu. Gözat'ı kullanarak bir belge seçilebilir (**...** ) düğmesi.  
  
 Bu özellik, yalnızca bir XSLT dosyası düzenleyici penceresinde şu anda etkin olduğunda görülebilir.  
  
 **Output**  
 XML belge dönüştürme çalıştırdığınızda oluşturulan dosya.  
  
 Bir dosya belirtilmezse, varsayılan dosya adı temel alınarak oluşturulur `method` özniteliği `xsl:output` öğesinin dosya uzantısı belirler. Varsayılan dosya, geçerli kullanıcının geçici dizininde bulunur.  
  
 **Şemaları**  
 Doğrulama yapmak için kullanılan şemalar. Düğme açar **XSD şemaları** iletişim kutusunda, kullanılacak şemaları seçmek için kullanılabilir.  
  
 Şema yolunu da girebilirsiniz. Birden çok şema belirtilmezse, her şema çift tırnak içine alınmalıdır.  
  
 **Stil sayfası**  
 Belgeyi dönüştürmek için kullanılan XSLT dosyası olduğunda **XSLT çıktıyı Göster** komutu kullanılır. Bu alan boşsa, **XSLT çıktıyı Göster** komutu kullanıldığında, sağlanan değer Düzenleyicisi kullanan `xml-stylesheet` işleme yönergesi belge veya sizden için dosya adı.  
  
 Farklı bir stil sayfası olması gerektiğini belirtmek için bir XSLT dosyası düzenlenirken, bu özellik kullanılabilir olduğunda kullanılabilir **XSLT çıktıyı Göster** veya **XSLT hata ayıklama** komut seçili. Örneğin, bir üst stil sayfasında bulunan bir stil sayfası düzenlerken bunu yapmak isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)   
 [XML Düzenleyicisi Bileşenleri](../xml-tools/xml-editor-components.md)



