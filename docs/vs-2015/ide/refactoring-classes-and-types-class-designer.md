---
title: Sınıfları ve türleri (Sınıf Tasarımcısı) yeniden düzenleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 215030b511ecbddbda23073df464035887f8ef95
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207968"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Sınıfları ve Türleri Yeniden Düzenleme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodunu yeniden düzenlediğinizde, daha kolay anlamanız, bakımını yapmak ve daha verimli iç yapısını ve nesnelerini şeklini değiştirerek tasarlanan, dış davranışı. Sınıf Tasarımcısı ve sınıf Ayrıntıları penceresinde, Visual Studio projenizde Visual C# .NET, Visual Basic .NET veya C++ kodunu yeniden düzenlediğinizde giriş olasılığını hataları ve yapmanız gereken iş miktarını azaltmaya yönelik kullanın.  
  
> [!NOTE]
>  Proje kaynak kodu denetiminde olması ve kullanıma alınmadı çünkü proje dosyaları salt okunur olabilir; Bu, başvurulan proje olur; veya kendi dosya diskte salt okunur olarak işaretlenmiş. Bu durumlardan biriyle projesinde çalışırken, projenin durumuna bağlı olarak çalışmanızı kaydetmek için çeşitli yollar sunulur. Bu, kodu yeniden düzenleme ve doğrudan düzenleme gibi başka bir yolla değiştirin kod geçerlidir. Daha fazla bilgi için [salt okunur bilgilerini görüntüleme (Sınıf Tasarımcısı)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|Destekleyici İçerik|  
|----------|------------------------|  
|**Sınıfları yeniden düzenleme:** sınıfı kısmi sınıflara bölme veya soyut temel sınıf uygulamak için yeniden düzenleme işlemleri kullanabilirsiniz.|-   [Nasıl yapılır: sınıfı kısmi sınıflara (Sınıf Tasarımcısı) bölme](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|  
|**Arabirimleri ile çalışma:** Sınıf Tasarımcısı'nda, uygulayabilirsiniz bir arabirim sınıf diyagramı üzerinde arabirim yöntemleri için kod sağlayan bir sınıf bağlanarak.|-   [Nasıl yapılır: arabirimi uygulama (Sınıf Tasarımcısı)](../ide/how-to-implement-an-interface-class-designer.md)|  
|**Türler, tür üyeleri ve parametreleri yeniden düzenleme:** Sınıf Tasarımcısı'nı kullanarak, türleri yeniden adlandırabilir, tür üyeleri geçersiz kılma veya bir türden diğerine taşıyabilirsiniz. Boş değer atanabilir türler de oluşturabilirsiniz.|-   [Türler ve tür üyeleri yeniden adlandırma](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Tür üyeleri bir türden diğerine taşıma](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Nasıl yapılır: boş değer atanabilir bir tür (Sınıf Tasarımcısı) oluşturma](../ide/how-to-create-a-nullable-type-class-designer.md)|  
  
###  <a name="RenamingTypesAndMembers"></a> Türler ve tür üyeleri yeniden adlandırma  
 Sınıf Tasarımcısı'nda, bir tür veya üye türü sınıf diyagramında veya Özellikler penceresinde yeniden adlandırabilirsiniz. Sınıf Ayrıntıları penceresinde üyesi ancak bir tür adını değiştirebilirsiniz. Bir tür veya tür üyesi yeniden adlandırılması, tüm windows ve eski adı burada görünen kod konumlarını yayar.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Sınıf tasarımcısında bir adı yeniden adlandırmak için  
  
1.  Sınıf diyagramında türe veya üyeye seçin ve adına tıklayın.  
  
     Üyenin adı düzenlenebilir hale gelir.  
  
2.  Türe veya üyeye türü için yeni adı yazın  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde bir adı yeniden adlandırmak için  
  
1.  Sınıf ayrıntıları penceresini görüntülemek için türü veya tür üyesi sağ tıklayın ve ardından **sınıf ayrıntıları**.  
  
     Sınıf Ayrıntıları penceresinde görüntülenir.  
  
2.  İçinde **adı** sütun türü üyesinin adını değiştirme  
  
3.  Hücreden odağı taşımak için basın **ENTER** anahtar veya uzak bir hücreye tıklayın.  
  
    > [!NOTE]
    >  Sınıf Ayrıntıları penceresinde üyesi ancak bir tür adını değiştirebilirsiniz.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Özellikler penceresinde bir adı yeniden adlandırmak için  
  
1.  Sınıf diyagramı veya sınıf Ayrıntıları penceresinde, türe veya üyeye sağ tıklayın ve ardından **özellikleri**.  
  
     Özellikler penceresinde görünür ve türü veya tür üyesi için özellikleri görüntüler.  
  
2.  İçinde **adı** özelliği türü adını değiştirin veya üye türü.  
  
     Tüm windows ve eski adı burada görünen kod konumlarını geçerli projede yeni adı yayar.  
  
###  <a name="MovingTypeMembers"></a> Tür üyeleri bir türden diğerine taşıma  
 Kullanarak **Sınıf Tasarımcısı**, her ikisi de geçerli sınıf diyagramında görünür olduğunda başka bir tür için tür üyesi bir türden diğerine taşıyabilirsiniz.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Bir tür üyesi bir türden diğerine taşımak için  
  
1.  Tasarım yüzeyinde görünür olan bir tür, başka bir türe taşıyın ve ardından istediğiniz üyeye sağ tıklayarak **Kes**.  
  
2.  Hedef türüne sağ tıklayın ve ardından **Yapıştır**.  
  
     Özellik kaynak türden kaldırılır ve hedef türünde görünür.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Türleri ve İlişkilendirmeleri Görüntüleme (Sınıf Tasarımcısı)](../ide/viewing-types-and-relationships-class-designer.md)||  
|[Sınıfları ve Türleri Tasarlama (Sınıf Tasarımcısı)](../ide/designing-classes-and-types-class-designer.md)||



