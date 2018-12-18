---
title: Denetimler ekleme ve bunların davranışlarını XAML Tasarımcısı'nda değiştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca377bcb37b44e1545d0502289217d331a495fae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179380"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>XAML Tasarımcısı'de denetimler ekleme ve bunların davranışlarını değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Denetimler, kullanıcıların uygulamanızla etkileşim kurmasına olanak sağlar. Bunları gerçekleştirmek için de bilgi toplamak için kullanabileceğiniz eylemler gibi bir nesneye animasyon ekleme veya bir veri kaynağı sorgu.  
  
 **Bu konuda:**  
  
-   [Çalışma yüzeyine denetimler ekleme](#Insert)  
  
-   [Denetimleri şeyler yap](#Modify)  
  
##  <a name="Insert"></a> Çalışma yüzeyine denetimler ekleme  
 Denetimlerden sürükleyebilirsiniz **varlıklar** üzerine panelinde **çalışma yüzeyine**ve bunları değiştirmek **özellikleri** penceresi.  
  
 ![Blend &#45; varlıklar &#45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")  
  
 Bu video bazı daha ortak denetimleri kullanma işlemini gösterir.  
  
|Denetim|Kısa bir video izleyin|  
|-------------|-------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [denetimler ekleme](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir düğme tasarım](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-ABCD-b0849edebada")|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir textblock için görüntüleri ekleme](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815C-e98c930ac189")|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir kaydırıcı ile bir araç ipucu oluşturma](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [GridSplitter ile çalışma](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Bir denetimi dışında bir resmi, şekli veya yol olun  
 Herhangi bir nesneyi bir denetime yapabilirsiniz.  
  
 ![Blend denetim haline Dönüştür iletişim kutusu](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")  
  
 Örneğin, bir sayfanın ortasında bir televizyon resmini düşünün. Denetimleri televizyon düğmeler gibi görünen küçük resimler yetersiz duruma gelir. Ardından, kullanıcıların kanalı değiştirmek için bu düğmeleri tıklayabilirsiniz.  
  
 Düğme denetimleri artık olduğundan, bu mümkündür. Denetimleri sayesinde, Kullanıcı etkileşimlerine karşılık vermelerini; Bu durumda kullanıcı bir düğmeyi tıkladığında.  
  
 Bir denetim yapmak için bir nesne seçin. Ardından **Araçları** menüsünde tıklatın **olun denetim**.  
  
##  <a name="Modify"></a> Denetimleri şeyler yap  
 Kullanıcılar bunlarla etkileşim kurduğunuzda denetimleri eylemleri gerçekleştirebilirsiniz. Örneğin, bunlar bir animasyon başlatabilir, bir veri kaynağını güncelleştirebilir veya bir videoyu oynatın.  
  
 Kullanım *Tetikleyicileri*, *davranışları*, ve *olayları* şeyler denetimleri yapma.  
  
### <a name="triggers"></a>Tetikleyiciler  
 A *tetikleyici* bir özelliğini değiştirir veya yanıt olarak bir olay ya da başka bir özellik değişikliği bir görevi gerçekleştirir. Örneğin, kullanıcılar üzerine geldiğinizde, bir düğme rengini değiştirebilirsiniz.  
  
 !["Tetikleyici" paneli](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir özellik tetikleyicisi Ekle](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>Davranışlar  
 A *davranışı* kod yeniden kullanılabilir bir pakettir. Bunu biraz yapmak birden fazla özelliklerini değiştirin. Bu sorgu veri hizmeti gibi eylemleri gerçekleştirebilirsiniz. Blend ile küçük bir koleksiyon bunların birlikte sunulur, ancak daha ekleyebilirsiniz. Bir davranış herhangi bir nesne, çalışma yüzeyine sürükleyin ve sonra davranış özelliklerini ayarlayarak özelleştirin.  
  
 ![Özellikler bölmesinde FluidMoveBehavior](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Blend ipuçları: 1. Bölüm davranışları kullanarak giriş](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Olaylar  
 Ultimate esneklik için tanıtıcı bir *olay*. Bazı kod yazmak zorunda kalırsınız.  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir fare olayına ekleyin](https://www.youtube.com/watch?v=2PMxAlb-x_E).



