---
title: Blend'de nesnelerin stilini değiştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 70bf451a828e3884a6004f6304b91351e866ee52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843656"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Blend'de nesnlerin stilini değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özellikleri ayarlamak için bir nesne özelleştirmek için en kolay yolu olan **özellikleri** bölmesi.  
  
 Ayarları yeniden kullanmak veya ayar gruplarını istiyorsanız, yeniden kullanılabilir bir kaynak oluşturun. Bunun bir *stili*, *şablon*, ya da özel bir renk gibi basit bir şeyden. Ayrıca, bir denetim üzerinde durumuna göre farklı şekilde görünür yapabilirsiniz. Örneğin, kullanıcı tıkladığında bir düğme yeşile döner.  
  
 **Bu konudaki**:  
  
-   [Fırçalar: nesnenin görünümünü değiştirme](#Brushes)  
  
-   [Stilleri ve şablonları: denetimler arasında tutarlı bir görünüm oluşturma](#Styles)  
  
-   [Görsel durumlar: kendi durumunu temel alan bir denetimin görünümünü değiştirme](#Visual)  
  
-   [Kaynaklar: renkleri, Stiller ve şablonlar oluşturma ve bunları daha sonra yeniden](#Resources)  
  
##  <a name="Brushes"></a> Fırçalar: nesnenin görünümünü değiştirme  
 Görünümünü değiştirmek istiyorsanız bir fırça bir nesneye uygulayın.  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Fırçalar Düzenleyicisi](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Yinelenen bir görüntü veya bir nesne üzerinde deseni boyama  
 Yinelenen bir görüntü veya bir nesne üzerinde deseni kullanılarak boyama bir *döşeme Fırçası*.  
  
 Döşeme Fırçası oluşturmak için oluşturarak başlayın bir *resim fırçası*, *çizim Fırçası*, veya *görsel fırça* kaynak.  
  
 Resim fırçası bir görüntü kullanarak oluşturun. Aşağıdaki çizimler resim fırçası ve döşemeli resim fırçası çevrilmiş resim fırçası göstermektedir.  
  
 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png " 38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 Çizim Fırçası bir vektör bir yol veya şekil gibi çizim kullanarak oluşturun. Aşağıdaki çizimler çizim Fırçası ve döşemeli çizim Fırçası çevrilmiş çizim Fırçası göstermektedir.  
  
 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png " 15bf6021-620c-4490-9eae-086153d3f14f")  
  
 Görsel bir fırçayı bir düğme gibi bir denetim oluşturun. Aşağıdaki çizimler görsel fırça ve döşemeli görsel fırça göstermektedir.  
  
 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [kutucuk Fırçalar](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Stilleri ve şablonları: denetimler arasında tutarlı bir görünüm oluşturma  
 Görünümünü ve davranışını bir kez tasarlayabilir ve ayrı ayrı tutmak zorunda kalmazsınız, tasarım diğer denetimlere uygulanır.  
  
 **Bir stil kullanmalısınız?** : (Örneğin, bir düğme rengi) varsayılan özellikleri ayarlamak istiyorsanız kullanmak bir *stil*. Bile sizin için bir stil uygulamış olduğunuz sonra bir denetim değiştirebilirsiniz.  
  
 **Bir şablonu kullanmalısınız?** : Bir denetimin yapısını değiştirmek istiyorsanız, kullanmak bir *şablon*. Bir grafik veya logosu, bir düğmeye dönüştürme olduğunu düşünün. Bir şablon uyguladığınız sonra bir denetim değiştiremezsiniz.  
  
### <a name="create-a-template-or-style"></a>Bir şablon veya stil oluşturma  
 Bir şablon oluşturmanın iki yolu vardır. Çalışma yüzeyindeki bir denetime herhangi bir nesneye dönüştürebilir veya varolan bir denetimi şablonunuzu temel alabilir.  
  
 Herhangi bir nesne için bir denetim şablonu dönüştürmek için nesneyi seçin ve ardından **Araçları** menüsünde seçin **denetim haline Dönüştür**.  
  
 Varolan bir denetimi, şablona istiyorsanız, çalışma yüzeyinde bir nesneyi seçin. Ardından, çalışma yüzeyinin üst kısmında içerik haritası düğmeyi seçin, **şablonu Düzen**ve ardından **kopya Düzenle** veya **oluşturma boş**.  
  
 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 Stil oluşturma, nesneyi seçin ve ardından **nesne** menüsünde seçin **stili Düzenle**ve ardından **kopya Düzenle** veya **boş oluşturma**.  
  
- Seçin **kopya Düzenle** varsayılan stil veya şablon denetimi ile başlatmak için.  
  
- Seçin **oluşturma boş** sıfırdan başlatmak için.  
  
  **Geçerli olanı Düzenle** seçeneği, yalnızca bir stil veya önceden oluşturduğunuz bir şablonu düzenlerseniz görüntülenir. Bir denetim için varsayılan sistem şablonunu yine de kullandığı görünmeyecektir.  
  
  İçinde **stil kaynağı oluştur** iletişim kutusu, ya da adını stil veya şablon daha sonra kullanabileceğiniz ya da bu türdeki tüm denetimlere stili veya şablonu uygulayabilirsiniz.  
  
  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
>  Stilleri veya şablonları her denetim türü için oluşturulamıyor. Bir denetim onları desteklemiyorsa, içerik haritası düğmesi çalışma yüzeyi üzerinde görünmez.  
>   
>  Ana belgenizin düzenleme kapsamına dönmek için tıklayın **kapsamına dönmek** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b").  
>   
>  ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [stil oluşturma](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [ifade Blend'de bir denetim şablonu oluşturma](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### <a name="apply-a-style-or-template-to-a-control"></a>Bir denetime stil veya şablon uygulama  
 Bir nesneye sağ [nesneler ve zaman çizelgesi](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelinde öğesini **şablonu Düzen**ve ardından **kaynağı Uygula**.  
  
 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>Varsayılan stil veya şablon denetiminin geri yükleme  
 İstediğiniz denetimi seçin ve [özellikleri](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57) paneli, bulun **stili** veya **şablon** özelliği. ' A tıklayarak **Gelişmiş Seçenekler** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb")ve ardından **sıfırlama** kısayol menüsünde.  
  
##  <a name="Visual"></a> Görsel durumlar: kendi durumunu temel alan bir denetimin görünümünü değiştirme  
 Denetimlerin kullanıcı denetimine göre farklı görsel görünümlerini olabilir. Örneğin, bir kullanıcı buna tıkladığında veya bir animasyon çalıştırabilir yeşile bir düğme yapabilirsiniz. Kısaltır veya geçişleri kullanarak görsel durumlar arasındaki süreyi uzatabilir.  
  
 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF denetimleri durumunu yöneten](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Kaynaklar: renkleri, Stiller ve şablonlar oluşturma ve bunları daha sonra yeniden  
 Her şey, projenizdeki bir kaynağa dönüştürebilirsiniz. Farklı yerlerde uygulamanızda yeniden bir nesne bir kaynaktır. Örneğin, bir renk bir kez oluşturun, bir kaynak yapın ve ardından bu renk birkaç nesnelerinde kullanın. Tüm bu nesneleri rengini değiştirmek için renk kaynağı değiştirmeniz yeterlidir.  
  
 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-B153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [kaynaklarla ilgili kısa bir touch](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)



