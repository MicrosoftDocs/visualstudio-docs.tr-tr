---
title: Hizmet başvurusu Yapılandır iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24da338378739afca6ad228582a29069aebde9f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266987"
---
# <a name="configure-service-reference-dialog-box"></a>Hizmet Başvurusu Yapılandırma İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
**Hizmet başvurusu yapılandırma** iletişim kutusu davranışını yapılandırmanızı sağlar [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Hizmetleri.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden içeri ve dışarı aktarma ayarları seçin. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Erişim için **hizmet başvurusu yapılandırma** iletişim kutusunda sağ tıklatıp hizmeti başvurusunun **Çözüm Gezgini** ve **hizmet başvurusu Yapılandır**. İletişim kutusunu tıklatarak da erişebilirsiniz **Gelişmiş** düğmesine **hizmet Başvurusu Ekle iletişim kutusunu**.  
  
## <a name="task-list"></a>Görev Listesi  
  
-   Bir WCF Hizmeti barındırıldığı adresini değiştirmek için yeni adresi girin. **adresi** alan.  
  
-   WCF istemci sınıfları için erişim düzeyini değiştirmek için bir erişim düzeyi anahtar sözcüğünü seçin **erişim sınıflar için erişim düzeyi** listesi.  
  
-   Zaman uyumsuz olarak bir WCF Hizmeti yöntemlerini çağırmak için seçin **zaman uyumsuz işlemler oluşturma** onay kutusu.  
  
-   Bir WCF İstemcisi'nde ileti anlaşması türleri oluşturmak için Seç **her zaman ileti anlaşmaları Oluştur** onay kutusu.  
  
-   Bir WCF istemcisi için liste veya sözlük koleksiyon türleri belirtmek için türlerinden seçin **koleksiyon türü** ve **zlük koleksiyon türü** listeler.  
  
-   Tür paylaşımı devre dışı bırakma, temizleme **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu. Tür başvurulan derlemeleri bir alt kümesi için paylaşımını etkinleştirmek için işaretleyin **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusunu seçin **belirtilen bütünleştirilmiş kodlardaki türleri yeniden**, istenen seçin başvurularının **başvurulan derlemelerin listesini**.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Adresi**  
 Web adresini güncelleştirmek için burada bir hizmet başvurusu için bir hizmet arar kullanılır. Örneğin, geliştirme sırasında hizmet bir geliştirme sunucusunda barındırılan ardından daha sonra bir üretim sunucusu için bir adres değişikliği araya taşındı.  
  
> [!NOTE]
>  Address öğesi ne zaman kullanılabilir olmayan **hizmet başvurusu yapılandırma** gelen iletişim kutusu görüntülenir **hizmet Başvurusu Ekle iletişim kutusunu**.  
  
 **Oluşturulan sınıflar için erişim düzeyi**  
 WCF istemci sınıfları için kod erişim düzeyini belirler.  
  
> [!NOTE]
>  Web sitesi projeleri için bu seçenek her zaman ayarlanır `Public` ve değiştirilemez. Daha fazla bilgi için [hizmet başvurularında sorun giderme](../data-tools/troubleshooting-service-references.md).  
  
 **Zaman uyumsuz işlemler oluşturma**  
 WCF hizmet yöntemleri zaman uyumlu olarak adlandırılan olup olmadığını belirler. (varsayılan) veya zaman uyumsuz olarak.  
  
 **Görev tabanlı işlemler oluştur**  
 Zaman uyumsuz kod yazarken, bu seçenek, görev paralel kitaplığı (sunulan TPL) .net 4 ile yararlanmanızı sağlar. Bkz: [görev paralel kitaplığı (TPL)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Her zaman ileti anlaşmaları oluştur**  
 İleti anlaşması türleri için bir WCF istemcisi oluşturulup oluşturulmayacağını belirler. İleti sözleşmeleri hakkında daha fazla bilgi için bkz: [kullanarak ileti sözleşmeleri](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).  
  
 **Koleksiyon türü**  
 Bir WCF istemcisi için liste koleksiyon türünü belirtir. Varsayılan türü <xref:System.Array>.  
  
 **Zlük koleksiyon türü**  
 Zlük koleksiyon türü için bir WCF istemcisi belirtir. Varsayılan türü <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Başvurulan bütünleştirilmiş kodlardaki türleri yeniden kullan**  
 Bir WCF istemcisi yeniden kullanmak zaten bir hizmet eklendiğinde veya güncelleştirildiğinde yeni türleri oluşturma yerine başvurulan derlemelerde deneyip denemeyeceğini belirler. Varsayılan olarak, bu seçenek denetlenir.  
  
 **Tüm başvurulan bütünleştirilmiş kodlardaki türleri yeniden kullan**  
 Seçili olduğunda, tüm türlerin **başvurulan derlemelerin listesini** mümkünse yeniden kullanılabilir. Varsayılan olarak, bu seçenek seçilidir.  
  
 **Belirtilen bütünleştirilmiş kodlardaki türleri yeniden kullan**  
 Seçili olduğunda, yalnızca seçilen türlerinde **başvurulan derlemelerin listesini** yeniden kullanılabilir.  
  
 **Başvurulan bütünleştirilmiş kodların listesi**  
 Proje veya Web sitesi için başvurulan derlemelerin bir listesini içerir. Zaman **belirtilen bütünleştirilmiş kodlardaki türleri yeniden** seçildiğinde, tek tek derlemeleri seçilen veya temizlenen.  
  
 **Web Başvurusu Ekle**  
 Görüntüler [NIB: Web Başvurusu Ekle iletişim kutusu](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Bu seçenek, 2.0 sürümünü hedefleyen projeler için kullanılması gereken [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  **Web başvurusu Ekle'yi** düğmesidir yalnızca **hizmet başvurusu yapılandırma** gelen iletişim kutusu görüntülenir **hizmet Başvurusu Ekle iletişim kutusunu**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu Kaldır](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Nasıl yapılır: Web hizmetine başvuru ekleme](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/configure-service-reference-dialog-box.md)

