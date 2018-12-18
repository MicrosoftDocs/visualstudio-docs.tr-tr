---
title: 'Nasıl yapılır: sınıf diyagramlarını özelleştirme (Sınıf Tasarımcısı) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a4b163aef25972968933d3352486aab9ebbf962
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950982"
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Nasıl Yapılır: Sınıf Diyagramlarını Özelleştirme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf diyagramlarının bilgileri görüntüleme biçimini değiştirebilirsiniz. Tüm diyagramı veya tasarım yüzeyinde tek tek türleri özelleştirebilirsiniz.  
  
 Örneğin, tüm bir sınıf diyagramının yakınlaştırma seviyesini ayarlayabilir, tek tek üyelerin gruplandırılma ve sıralanma şeklini değiştirebilir, ilişkileri gizleyebilir ya da gösterebilir ve tek tek türleri ya da tür kümelerini diyagram üzerinde istediğiniz yere taşıyabilirsiniz.  
  
> [!NOTE]
>  Şekillerin diyagram üzerinde görünme biçimi özelleştirildiğinde, diyagramda temsil edilen türlerin temelini oluşturan kod değişmez.  
  
 Tür üyelerini içeren bölümlere (bir sınıf içindeki Özellikler bölümü gibi) bölmeler adı verilir. Tek tek bölmeleri ve tür üyelerini gizleyebilir veya gösterebilirsiniz.  
  
 **Bu konudaki**  
  
-   [Sınıf diyagramını yakınlaştırma ve uzaklaştırma](../ide/how-to-customize-class-diagrams-class-designer.md#ZoomInOut)  
  
-   [Gruplandırma ve tür üyelerinin sıralamasını özelleştirme](../ide/how-to-customize-class-diagrams-class-designer.md#CustomizeGroupingSorting)  
  
-   [Türe göre bölmeleri gizleme](../ide/how-to-customize-class-diagrams-class-designer.md#HideCompartments)  
  
-   [Türe göre tek tek üyeleri gizleme](../ide/how-to-customize-class-diagrams-class-designer.md#HideMembers)  
  
-   [Türe göre gizli bölmeleri ve üyeleri gösterme](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayHiddenCompartmentsAndMemberrs)  
  
-   [İlişkileri gizleme](../ide/how-to-customize-class-diagrams-class-designer.md#HideAssociationAndInheritance)  
  
-   [Gizli ilişkileri gösterme](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayAssociationAndInheritance)  
  
-   [Bir sınıf diyagramından şekil kaldırma](../ide/how-to-customize-class-diagrams-class-designer.md#RemoveCodeAndShape)  
  
-   [Bir tür şeklini ve temelini oluşturan kodu silme](../ide/how-to-customize-class-diagrams-class-designer.md#DeleteTypeShapeAndCode)  
  
##  <a name="ZoomInOut"></a> Sınıf diyagramını yakınlaştırma ve uzaklaştırma  
  
1.  Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.  
  
2.  Sınıf Tasarımcısı araç çubuğunda **Yakınlaştır** veya **Uzaklaştır** Tasarımcı yüzeyinin yakınlaştırma seviyesini değiştirmek için.  
  
     veya  
  
     Belirli bir yakınlaştırma değeri belirtin. Kullanabileceğiniz **yakınlaştırma** açılan liste veya geçerli bir yakınlaştırma seviyesi girebilirsiniz (geçerli aralık: % 10 ile 400 arasında).  
  
    > [!NOTE]
    >  Yakınlaştırma seviyesinin değiştirilmesi sınıf diyagramı çıktınızın ölçeğini etkilemez.  
  
##  <a name="CustomizeGroupingSorting"></a> Gruplandırma ve tür üyelerinin sıralamasını özelleştirme  
  
1.  Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.  
  
2.  Tasarım yüzeyinde boş bir alana sağ tıklayın ve fareyle **Grup üyeleri**.  
  
3.  Kullanılabilir seçeneklerden birini belirtin:  
  
    1.  **Göre grupla** tek tek tür üyelerini gruplandırılmış bir özellikleri, yöntemleri, olaylar ve alanlar listesi ayırır. Tek tek gruplar varlıklar tanımına göre değişir: Örneğin, bir sınıf için henüz hiç tanımlı olay yoksa, bu sınıf olaylar grubunu görüntülemez.  
  
    2.  **Erişimine göre grupla** erişim değiştiricilerine göre üyenin üzerinde tek tek tür üyelerini gruplandırılmış bir liste halinde ayırır. Örneğin, Genel ve Özel.  
  
    3.  **Alfabetik olarak Sırala** tek bir alfabetik liste olarak bir varlığı oluşturan öğeleri görüntüler. Liste artan düzende sıralanır.  
  
##  <a name="HideCompartments"></a> Türe göre bölmeleri gizleme  
  
1.  Sınıf tasarımcısında bir sınıf diyagramı dosyasını açın ve seçin.  
  
2.  Özelleştirmek istediğiniz türde üye kategorisine sağ tıklayın (örneğin, **yöntemleri** düğümünde bir sınıf.  
  
3.  Tıklayın **Gizle bölme**.  
  
     Seçili bölme tür kapsayıcısından kaybolur.  
  
##  <a name="HideMembers"></a> Türe göre tek tek üyeleri gizleme  
  
1.  Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.  
  
2.  Gizlemek istediğiniz türde üyeye sağ tıklayın.  
  
3.  Tıklayın **Gizle**.  
  
     Seçili üye tür kapsayıcısından kaybolur.  
  
##  <a name="DisplayHiddenCompartmentsAndMemberrs"></a> Türe göre gizli bölmeleri ve üyeleri gösterme  
  
1.  Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.  
  
2.  Gizli bölmeyi içeren türün adına sağ tıklayın.  
  
3.  Tıklayın **tüm üyeleri Göster**.  
  
     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.  
  
##  <a name="HideAssociationAndInheritance"></a> İlişkileri gizleme  
  
1.  Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.  
  
2.  Gizlemek istediğiniz ilişkilendirme veya devralma çizgisine sağ tıklayın.  
  
3.  Tıklayın **Gizle** ilişkilendirme çizgileri seçeneğine tıklayıp için **devralım çizgisi Gizle** devralım çizgileri içinse.  
  
4.  Tıklayın **tüm üyeleri Göster**.  
  
     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.  
  
##  <a name="DisplayAssociationAndInheritance"></a> Gizli ilişkileri gösterme  
  
1. Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.  
  
2. Gizli ilişkilendirmeyi veya devralmayı içeren türün adına sağ tıklayın.  
  
   Tıklayın **tüm üyeleri Göster** ilişkilendirme çizgileri seçeneğine tıklayıp için **temel sınıfı Göster** veya **türetilmiş sınıfları Göster** devralım çizgileri içinse.  
  
##  <a name="RemoveCodeAndShape"></a> Bir sınıf diyagramından şekil kaldırma  
 Türün temelini oluşturan koda etkisi olmaksızın, bir tür şeklini sınıf diyagramından kaldırabilirsiniz. Tür şekillerinin bir sınıf diyagramından kaldırılması yalnızca o diyagramı etkiler: Türü tanımlayan temel kod ve türü görüntüleyen diğer diyagramlar bundan etkilenmez.  
  
1.  Sınıf diyagramında, diyagramdan kaldırmak istediğiniz tür şeklini seçin.  
  
2.  Üzerinde **Düzenle** menüsünde seçin **diyagramdan Kaldır**.  
  
     Tür şekli ve varsa bu şekle bağlı ilişkilendirme ya da devralma çizgileri bundan böyle diyagramda görünmez.  
  
##  <a name="DeleteTypeShapeAndCode"></a> Bir tür şeklini ve temelini oluşturan kodu silme  
  
1.  Tasarım yüzeyinde şekle sağ tıklayın.  
  
2.  Seçin **kodu Sil** bağlam menüsünden.  
  
     Şekil diyagramdan kaldırılır ve temelini oluşturan kod projeden silinir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sınıf diyagramları (Sınıf Tasarımcısı) ile çalışma](../ide/working-with-class-diagrams-class-designer.md)   
 [Nasıl yapılır: üye gösterimi ile ilişkilendirme gösterimi (Sınıf Tasarımcısı) arasında](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)   
 [Nasıl yapılır: Varolan türleri görüntüleme (Sınıf Tasarımcısı)](../ide/how-to-view-existing-types-class-designer.md)   
 [Türleri ve İlişkilendirmeleri Görüntüleme (Sınıf Tasarımcısı)](../ide/viewing-types-and-relationships-class-designer.md)



