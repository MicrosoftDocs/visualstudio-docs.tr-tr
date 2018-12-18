---
title: Model Gezginini özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 77999eea0a76088368ff5e7ee66f9088dc45efa5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175948"
---
# <a name="customizing-the-model-explorer"></a>Model Gezginini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçin etki alanına özgü dil Tasarımcısı görünümünü ve davranışını Gezginin şu şekilde değiştirebilirsiniz:  
  
-   Pencere Başlığı değiştirin.  
  
-   Tab simgesi değiştirin.  
  
-   Düğümler için simgeler olarak değişir.  
  
-   Düğümleri gizleme.  
  
## <a name="changing-the-window-title"></a>Pencere başlığını değiştirme  
 Oluşturulan Gezgini'nin pencere başlığı değiştirmek için seçin **Gezgin davranışı** içinde **DSL Gezgini**ve ardından **özellikleri** penceresinde  **Başlık** özelliğini istediğiniz başlığı.  
  
## <a name="changing-the-tab-icon"></a>Sekme simgesini değiştirme  
 Explorer için sekmesinde simgesi değiştirmek için 16 x 16 piksel simgesi .bmp dosyasında kullanın. Simge dosyası \DslPackage\Resources\ klasöre yerleştirin ve ardından için dosya adını değiştirerek **ModelExplorerToolWindowBitmaps.bmp**. Örneğin, değişebilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] setup.ico simge dosyası .bmp biçimine ve yeniden adlandırın **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. İle birlikte yerleştirildiğinde oluşturulan tasarımcının gezgininizde sekmesinde bu simge görüntülemek **Çözüm Gezgini**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Özel simgeleri Gezgini düğümlerinde ayarlama  
 Gezgin düğümü ayarlarını kullanarak düğümleri gezgininizde özelleştirebilirsiniz. Aşağıdaki yordamda, bir düğüm için bir simge eklemek gösterilmektedir.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Bir Gezgini düğümü için bir simge eklemek için  
  
1.  Oluşturma bir [!INCLUDE[dsl](../includes/dsl-md.md)] Görev akışı çözüm şablonunu kullanarak çözüm.  
  
2.  Bir 16 x 16 piksel simgesi içeren bir .bmp dosyası yerleştirme **Dsl\Resources** çözüm klasöründe.  
  
3.  İçinde **DSL Gezgini**, sağ **Gezgin davranışı** ve ardından **ekleme Yeni Gezgin düğümü ayarlarını**.  
  
     Bir **ExplorerNodeSettings** düğümü altında görünür **özel düğüm ayarları** düğümü.  
  
4.  Seçin **ExplorerNodeSettings**ve ardından **özellikleri** penceresinde **sınıfı** için **aktör**.  
  
5.  Ayarlama **görüntülenecek simge** simge dosyasının yolu.  
  
6.  Tüm Şablonları Dönüştür ve derleme ve çözümü çalıştırın.  
  
7.  Oluşturulan tasarımcıda örnek diyagramı açın.  
  
     Gezgin üç göstermelidir **aktör** simge olan düğümleri.  
  
> [!NOTE]
>  Oluşturulan Gezgini'nde görüntülenen herhangi bir öğe için bir düğüm simgesi ayarlarsanız, tüm Gezgini düğümleri simgesi görüntüler. Herhangi bir simge ayarlarsanız düğümleri varsayılan simge görüntüler.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Bir Gezgini düğümünde görüntülenen adını değiştirme  
 Model öğelerinin adlarını gezgininizde nasıl görüntüleneceğini değiştirebilirsiniz. Aşağıdaki yordamı, adını görüntülemek gösterilmektedir **görev** tarafından başvurulan bir **yorum** açıklama düğümünde.  
  
#### <a name="to-display-a-property"></a>Bir özelliği görüntülemek için  
  
1.  Önceki yordamda oluşturduğunuz çözümü açın.  
  
2.  Emin olun **yorum** yalnızca bir tek etki alanı sınıfı, özellik adı ile rol'ün çoğulluğunun ayarlayarak başvuruyor **konuları** 0.. 1. Özellik adı olması gerektiğini **konu**, ve ilişki adı olması gerektiğini **CommentReferencesSubject**.  
  
3.  İçinde **DSL Gezgini**, sağ **Gezgin davranışı** ve ardından **ekleme Yeni Gezgin düğümü ayarlarını**.  
  
     Bir **ExplorerNodeSettings** düğümü altında görünür **özel düğüm ayarları** düğümü.  
  
4.  Seçin **ExplorerNodeSettings**ve ardından **özellikleri** penceresinde **sınıfı** için **yorum**.  
  
5.  Sağ **yorum** düğümünü ve ardından **yeni özellik yolu Ekle**.  
  
     Adlı yeni bir düğüm görünür **özelliği görüntülenen**.  
  
6.  Seçin **özelliği görüntülenen**ve ardından **özellikleri** penceresinde Değer alanını tıklatın **yolu için özellik**. Seçin **yorum**, ardından **CommentReferencesSubject**, ardından **FlowElement**. Sonuçlanan yolunu benzemelidir **CommentReferencesSubject.Subject/! Konu**.  
  
7.  Değer alanında **özelliği**seçin **adı**.  
  
8.  Tüm Şablonları Dönüştür ve sonra çözümünüzün çalıştırın.  
  
9. Oluşturulan tasarımcıda örnek diyagramı açın.  
  
10. Çizim bir **açıklama bağlayıcı** yorum öğe arasında ve **Task1** öğeyi diyagram üzerinde.  
  
     Gezgin düğümünü açıklama olarak görüntülenmelidir **Task1**.  
  
## <a name="hiding-nodes"></a>Düğümleri gizleme  
 Kendi yoluna ekleyerek bir düğüm gezgininizde gizleyebilirsiniz **gizli düğümleri** düğümünün **DSL Gezgini**. Aşağıdaki yordam nasıl gizleneceği gösterilmektedir **yorum** düğümleri.  
  
#### <a name="to-hide-an-explorer-node"></a>Gezgini düğümü gizlemek için  
  
1.  Önceki yordamda oluşturduğunuz çözümü açın.  
  
2.  İçinde **DSL Gezgini**, sağ **Gezgin davranışı** ve ardından **yeni etki alanı yolu Ekle**.  
  
     A **etki alanı yolu** düğümü altında görünür **gizli düğümleri**.  
  
3.  Seçin **etki alanı yolu**ve ardından **özellikleri** penceresinde Değer alanını tıklatın **yol tanımı**. Seçin **FlowGraph**, ardından **FlowGraphHasComments**. Sonuçlanan yolunu benzemelidir **FlowGraphHasComments.Comments**  
  
4.  Tüm Şablonları Dönüştür ve sonra çözümünüzün çalıştırın.  
  
5.  Oluşturulan tasarımcıda örnek diyagramı açın.  
  
     Explorer yalnızca göstermelidir bir **aktörler** düğümünü ve değil gösterilip gösterilmeyeceğini **açıklamaları** düğümü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



