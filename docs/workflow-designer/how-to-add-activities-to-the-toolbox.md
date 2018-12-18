---
title: 'İş Akışı Tasarımcısı - nasıl yapılır: etkinlikler araç kutusuna ekleme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a009f36152163e3ac23b85deac4ea99f26092be9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118219"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Nasıl yapılır: etkinlikler araç kutusuna ekleme

Etkinlikler eklenebilir **araç** birkaç farklı şekilde, çözümünüzdeki. Bunlardan içinde geçerli projenize ekleme, farklı bir projedeki başvuru veya farklı bir derleme başvurusu.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Bir aktiviteyi geçerli projenize içinden eklemek için

1.  Yeni bir özel Etkinlik geçerli iş akışı projenize ekleyin. Projeniz için yeni bir özel etkinlik ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir iş akışı projesine yeni öğe eklemek](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Özel mantık, etkinliği ekleyin.

3.  Projeyi oluşturun. Yapı başarılı olursa yeni bir kategori **araç** adlı "\<*proje adı*>" Bu kategoride yer alan özel etkinlik birlikte görüntülenir.

    > [!NOTE]
    > Araç kutusu sıfırlarsanız, çözümü yeniden oluşturulmuş olsa bile özel etkinlikler kaldırılır. Özel etkinlikler araç kutusu sıfırlandı sonra yeniden için Visual Studio'yu yeniden başlatın.

    > [!NOTE]
    > Araç kutusu yalnızca belirli bir ada bir etkinliğin gösterebilir. İki etkinlik farklı derlemelerden aynı sınıf adı varsa, yalnızca biri görüntülenir.

    > [!NOTE]
    > Uygulama etki alanı Düzenleyicisi örnekler arasında paylaşılan; statik değişkenler kullandıysanız, de Düzenleyicisi örnekler arasında paylaşılır. Bu, istenen davranışı değilse, bir hizmet değişken örneklerini izlemek için kullanılmalıdır. Bkz: [ModelItem düzenleme bağlamı kullanarak](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) Tasarımcısı'nda Hizmetleri kullanma hakkında bilgi için.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Farklı bir projede etkinliği eklemek için

1.  En az bir iş akışı projesinde ve bir özel etkinlik kitaplığı projesi veya özel bir aktivite tanımlar başka bir iş akışı projesinde içeren bir çözüm açın.

2.  Her iki proje oluşturun. Derlemeleri başarılıysa, yeni bir kategori **araç** adlı "\<*proje adı*>" Bu kategoride yer alan özel etkinlik birlikte görüntülenir.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Bir derlemeye ait Araç Kutusu'na etkinlik eklemek için

1.  Bir iş akışı çözümü açın.

2.  Gelen **Araçları** menüsünde, select **araç kutusu öğelerini Seç**.

3.  İçinde **araç kutusu öğelerini Seç** iletişim kutusunda **System.Activities bileşenleri** sekmesinde ardından tıklatın **Gözat** özel içeren derlemeye gitmek için eklemek istediğiniz etkinliği.

4.  Derleme seçin ve tıklatın **Tamam**. Özel Etkinlik bileşeni bileşenleri listesine eklenir ve otomatik olarak seçilir.

    1.  Tıklatın **Tamam** iletişim kutusunu kapatmak için.

5.  Araç kutusunu görüntülemek için seçin **araç** gelen **Görünüm** menüsü.

6.  Özel Etkinlik görünür **araç** öğe eklenmeden önce odakta kategorisi altında. Örneğin, varsa **genel** kategori seçilmedi **araç** araç kutusu öğesi eklemeden önce etkinlik altında görünür **genel** kategorisi.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](../workflow-designer/using-the-workflow-designer.md)