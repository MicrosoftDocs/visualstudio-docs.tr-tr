---
title: Hizmet Başvurusu Yapılandırma İletişim Kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f0cb2737356813a9b637d7f16e9d5cda704c022a
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389506"
---
# <a name="configure-service-reference-dialog-box"></a>Hizmet Başvurusu Yapılandır iletişim kutusu

**Hizmet başvurusu yapılandırma** iletişim kutusu Windows Communication Foundation (WCF) hizmetlerini davranışını yapılandırmanıza olanak sağlar.

Erişim için **hizmet başvurusu yapılandırma** iletişim kutusunda sağ tıklatıp hizmeti başvurusunun **Çözüm Gezgini** ve **hizmet başvurusu Yapılandır**. İletişim kutusunu tıklatarak da erişebilirsiniz **Gelişmiş** düğmesine **hizmet Başvurusu Ekle iletişim kutusunu**.

## <a name="task-list"></a>Görev listesi

- Bir WCF Hizmeti barındırıldığı adresini değiştirmek için yeni adresi girin. **adresi** alan.

- WCF istemci sınıfları için erişim düzeyini değiştirmek için bir erişim düzeyi anahtar sözcüğünü seçin **erişim sınıflar için erişim düzeyi** listesi.

- Zaman uyumsuz olarak bir WCF Hizmeti yöntemlerini çağırmak için seçin **zaman uyumsuz işlemler oluşturma** onay kutusu.

- Bir WCF İstemcisi'nde ileti anlaşması türleri oluşturmak için Seç **her zaman ileti anlaşmaları Oluştur** onay kutusu.

- Bir WCF istemcisi için liste veya sözlük koleksiyon türleri belirtmek için türlerinden seçin **koleksiyon türü** ve **zlük koleksiyon türü** listeler.

- Tür paylaşımı devre dışı bırakma, temizleme **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu. Tür başvurulan derlemeleri bir alt kümesi için paylaşımını etkinleştirmek için işaretleyin **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusunu seçin **belirtilen bütünleştirilmiş kodlardaki türleri yeniden**, istenen seçin başvurularının **başvurulan derlemelerin listesini**.

## <a name="uielement-list"></a>UIElement listesi

 **Adresi**

 Burada bir hizmet başvurusu için bir hizmet arar web adresini güncelleştirir. Örneğin, geliştirme sırasında hizmet bir geliştirme sunucusu üzerinde barındırılan ve ardından bir üretim sunucusu için bir adres değişikliği araya taşınır.

> [!NOTE]
> Address öğesi ne zaman kullanılabilir olmayan **hizmet başvurusu yapılandırma** gelen iletişim kutusu görüntülenir **hizmet Başvurusu Ekle iletişim kutusunu**.

 **Oluşturulan sınıflar için erişim düzeyi**

 WCF istemci sınıfları için kod erişim düzeyini belirler.

> [!NOTE]
> Web sitesi projeleri için bu seçenek her zaman ayarlanır `Public` ve değiştirilemez. Daha fazla bilgi için [hizmet başvurularında sorun giderme](../data-tools/troubleshooting-service-references.md).

 **Zaman uyumsuz işlemler oluşturma**

 WCF hizmet yöntemleri çağrıldığında olup olmadığını zaman uyumlu olarak belirler (varsayılan) veya zaman uyumsuz olarak.

 **Görev tabanlı işlemler oluştur**

 Zaman uyumsuz kod yazarken, bu seçenek, görev paralel kitaplığı (sunulan TPL) .NET 4 yararlanmanıza olanak tanır. Bkz: [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Her zaman ileti anlaşmaları oluştur**

 İleti anlaşması türleri için bir WCF istemcisi oluşturulan olup olmadığını belirler. İleti sözleşmeleri hakkında daha fazla bilgi için bkz: [ileti anlaşmaları kullanma](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Koleksiyon türü**

 Bir WCF istemcisi için liste koleksiyon türünü belirtir. Varsayılan türü <xref:System.Array>.

 **Zlük koleksiyon türü**

 Zlük koleksiyon türü için bir WCF istemcisi belirtir. Varsayılan türü <xref:System.Collections.Generic.Dictionary%602>.

 **Başvurulan bütünleştirilmiş kodlardaki türleri yeniden kullan**

 Bir WCF istemcisi hizmet eklendiğinde veya güncelleştirildiğinde yeni türleri oluşturma yerine başvurulan derlemelerde ne zaten var. yeniden dener olup olmadığını belirler. Varsayılan olarak, bu seçenek denetlenir.

 **Tüm başvurulan bütünleştirilmiş kodlardaki türleri yeniden kullan**

 Seçili olduğunda, tüm türlerin **başvurulan derlemelerin listesini** mümkünse tanımlarlar. Varsayılan olarak, bu seçenek seçilidir.

 **Belirtilen bütünleştirilmiş kodlardaki türleri yeniden kullan**

 Seçili olduğunda, yalnızca seçilen türlerinde **başvurulan derlemelerin listesini** tanımlarlar.

 **Başvurulan bütünleştirilmiş kodların listesi**

 Proje veya Web sitesi için başvurulan derlemelerin bir listesini içerir. Seçtiğinizde, **belirtilen bütünleştirilmiş kodlardaki türleri yeniden**, seçebilir veya ayrı ayrı derlemeler temizleyin.

 **Web Başvurusu Ekle**

 Görüntüler **Web başvurusu Ekle'yi** iletişim kutusu.

> [!NOTE]
> Bu seçenek yalnızca 2.0 sürümünü hedefleyen projeler için kullanılması gereken [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].
>
> [!NOTE]
> **Web başvurusu Ekle'yi** düğmesi kullanılabilir yalnızca zaman **hizmet başvurusu yapılandırma** gelen iletişim kutusu görüntülenir **hizmet Başvurusu Ekle iletişim kutusunu**.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: web hizmetine başvuru ekleme](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/configure-service-reference-dialog-box.md)