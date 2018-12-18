---
title: 'Nasıl yapılır: bir Atom oluşturmak için özel bir galeriyi akış | Microsoft Docs'
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
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f720c4297ab2ff31abe90365b0e25209762dba1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789688"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Nasıl yapılır: bir Atom oluşturmak için özel bir galeriyi akışı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Atom (uzantıları içeren ve akışa ekleme bir intranet konumu için RSS akışı) oluşturabileceğiniz **Uzantılar ve güncelleştirmeler** özel bir galeri olarak. Daha fazla bilgi için [özel galeriler](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Oluşturma bir Atom akışı  
 Atom akışı özel bir galeri oluşturmak için öncelikle bir klasöre uzantılarınızı (.vsix dosyaları) toplamanız gerekir. İsterseniz, alt klasörler halinde düzenleyebilirsiniz. Ayrıca, aşağıdaki kaynakları gerekir:  
  
- Uzantıları özel bir galeri kullanılabilmesini atom.xml dosyası. Atom.xml dosyaya bağlanma hakkında daha fazla bilgi için **Uzantılar ve güncelleştirmeler**, bkz: [özel galeriler](../extensibility/private-galleries.md).  
  
- (Örneğin, ekran görüntüleri) extensions ayıklanan herhangi bir görüntü dosyalarını içeren bir klasör. Böylece yer alır, görüntü yollarında göreli bağlantıları atom.xml dosyayı içeren **Uzantılar ve güncelleştirmeler**.  
  
  Örneğin, bir klasöre toplanan aşağıdaki iki uzantıları varsayın:  
  
- Template_Wizard_239.vsix boş bir VSIX proje şablonudur.  
  
- SelectionHighlight.vsix Seçili sözcüğün tüm örneklerinin vurgulamak için bir araçtır.  
  
  Atom.xml dosyasının içeriğini aşağıdaki örneğe benzer:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 Görüntüleri oluşturulan bir klasörde ekran görüntüleri için dikkat edin iki bağlantı etiketlerini bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Galeriler](../extensibility/private-galleries.md)

