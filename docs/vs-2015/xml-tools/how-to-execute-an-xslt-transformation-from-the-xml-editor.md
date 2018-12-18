---
title: 'Nasıl yapılır: XML düzenleyicisinden XSLT dönüştürmesi yürütme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 358c799c0ef6cd6ab90f64e5025376141ff534c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245290"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Nasıl yapılır: XML düzenleyicisinden XSLT dönüştürmesi yürütme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Düzenleyicisi'ni dönüştürmeyi gerçekleştirmek ve çıktısını görüntülemek bir XSLT stil sayfası bir XML belgesi ile ilişkilendirmenizi sağlar. XSLT dönüşümü sonuç çıktısı, yeni bir belge penceresi görüntülenir.  
  
 **Çıkış** özellik çıkış dosya adını belirtir. Varsa **çıkış** özelliği boşsa, bir dosya adı, geçici dizin oluşturulur. Dosya uzantısı dayanır `xsl:output` öğesi, stil sayfası ve .xml, .txt veya .htm olabilir.  
  
 Varsa **çıkış** özelliği, bir dosya adı ile bir .htm belirtir ya da .html uzantısı, XSLT çıkış önizlemesi kullanarak [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Diğer tüm dosya uzantıları tarafından seçilen varsayılan Düzenleyicisi kullanılarak açılan [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio. Örneğin, .xml dosya uzantısı ise Visual Studio XML Düzenleyicisi'ni kullanır.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Bir XML belgesinden XSLT dönüştürmesi yürütme için  
  
1.  Bir XML belgesi bir XML düzenleyicisinde açın.  
  
2.  Bir XSLT stil sayfası XML belge ile ilişkilendirin.  
  
    -   Ekleme bir `xml-stylesheet` işleme yönergesi için XML belgesi. Örneğin, aşağıdaki satırı ekleyin `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` için belge giriş.  
  
         veya  
  
    -   XSLT stil sayfası kullanılarak ekleme **özellikleri** penceresi. Belgedeki **Özellikler penceresi**, tıklayın **Gözat** için düğme **stil sayfası** alan, XSLT stil sayfası seçin ve tıklayın **açın**.  
  
3.  Tıklayın **ShowXSL çıkış** düğmesini **XML Düzenleyicisi** araç çubuğu.  
  
    > [!NOTE]
    >  XML belge ile ilişkilendirilmiş hiç stil sayfası varsa, bir iletişim kutusu kullanmak için stil sayfası girmenizi ister.  
    >   
    >  XSLT dönüşümü sonuç çıktısı, yeni bir belge penceresi görüntülenir.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Bir XSLT stil sayfasındaki XSLT dönüştürmesi yürütme için  
  
1.  Bir XSLT stil sayfası XML düzenleyicisinde açın.  
  
2.  Bir XML belgesinde belirtin **giriş** belge alanını **özellikleri** penceresi.  
  
    > [!NOTE]
    >  XML belge dönüştürme için kullanılan giriş belgesidir. XSLT dönüşümü başlatıldığında, bir belge belirtilmezse **Dosya Aç** iletişim kutusu görünür ve o anda bir belge belirtebilirsiniz.  
  
3.  Tıklayın **ShowXSLT çıkış** düğmesini **XML Düzenleyicisi** araç çubuğu.  
  
     XSLT dönüşümü sonuç çıktısı, yeni bir belge penceresi görüntülenir.  
  
### <a name="to-provide-a-different-output-file-name"></a>Farklı çıkış dosyası adı sağlamak için  
  
1.  Bir dosya adı belirtin **çıkış** belge alanını **özellikleri** penceresi.  
  
2.  Tıklayın **ShowXSLT çıkış** düğmesini **XML Düzenleyicisi** araç çubuğu.  
  
     XSLT dönüşümü sonuç çıktısı, yeni bir belge penceresi görüntülenir ve çıkış penceresinde kullanılan Düzenleyicisi'nin dosya uzantısını üzerinde bağlıdır, **çıkış** belge özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)



