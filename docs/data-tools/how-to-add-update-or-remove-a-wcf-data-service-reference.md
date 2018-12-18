---
title: 'Nasıl Yapılır: WCF Veri Hizmeti Başvurusunu Güncelleme veya Kaldırma'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9099c1ee0b1ed3af108c11792f7629453dfbf7c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819049"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Nasıl yapılır: ekleme, güncelleştirme veya bir WCF veri hizmeti başvurusunu Kaldır
A *hizmet başvurusu* bir projeye bir veya daha fazla erişim sağlayan [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Kullanım **hizmet Başvurusu Ekle** aramak için iletişim kutusu [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] geçerli çözümde, yerel olarak bir yerel ağ veya Internet üzerinde.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Bir hizmet Başvurusu Ekle

### <a name="to-add-a-reference-to-an-external-service"></a>Bir dış hizmet için bir başvuru eklemek için

1.  İçinde **Çözüm Gezgini**, hizmeti eklemek ve ardından istediğiniz proje adına sağ tıklayın **hizmet Başvurusu Ekle**.

     **Hizmet Başvurusu Ekle** iletişim kutusu görüntülenir.

2.  İçinde **adresi** kutusuna hizmeti için URL girin ve ardından **Git** hizmet için aranacak. Hizmet kullanıcı adı ve parola güvenlik uygularsa, bir kullanıcı adı ve parolası istenebilir.

    > [!NOTE]
    >  Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır. Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.

     URL'den belirleyebilirsiniz **adresi** listesinde, geçerli hizmet meta verileri bulundu önceki 15 URL depolar.

     Arama yapılırken bir ilerleme çubuğu görüntülenir. Tıklayarak arama dilediğiniz zaman durdurabilirsiniz **Durdur**.

3.  İçinde **Hizmetleri** listesinde, bir varlık kümesi seçin ve istediğiniz hizmeti düğümünü genişletin.

4.  İçinde **Namespace** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

5.  Tıklayın **Tamam** projesine başvuru eklenemiyor.

     Bir hizmeti istemcisi (proxy) oluşturulur ve hizmet açıklayan meta veriler eklenir *app.config* dosya.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Geçerli çözümde bir hizmet başvurusu eklemek için

1. İçinde **Çözüm Gezgini**, hizmeti eklemek ve ardından istediğiniz proje adına sağ tıklayın **hizmet Başvurusu Ekle**.

    **Hizmet Başvurusu Ekle** iletişim kutusu görüntülenir.

2. Tıklayın **Bul**.

    Tüm hizmetler (her ikisi de [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ve WCF hizmetleri) geçerli çözümde eklenen **Hizmetleri** listesi.

3. İçinde **Hizmetleri** listesinde, bir varlık kümesi seçin ve istediğiniz hizmeti düğümünü genişletin.

4. İçinde **Namespace** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

5. Tıklayın **Tamam** projesine başvuru eklenemiyor.

    Bir hizmeti istemcisi (proxy) oluşturur ve hizmet açıklayan meta veriler eklenir *app.config* dosya.

## <a name="update-a-service-reference"></a>Hizmet başvurusunu güncelle
 Varlık veri modeli için bir [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] bazen değiştirir. Bu durumda, hizmet başvurusunu güncelleştirmeniz gerekir.

### <a name="to-update-a-service-reference"></a>Bir hizmet başvurusu güncelleştirilecek

-   İçinde **Çözüm Gezgini**, hizmet başvurusunu sağ tıklayın ve ardından **güncelleştirme hizmet başvurusu**.

     Başvuru özgün konumundan güncelleştirilir ve hizmeti istemcisi meta verilerindeki değişiklikleri yansıtacak şekilde yeniden ilerleme durumu iletişim kutusu görüntülenir.

## <a name="remove-a-service-reference"></a>Hizmet başvurusunu Kaldır
 Bir hizmet başvurusu artık kullanılıyorsa çözümünüzden kaldırabilirsiniz.

### <a name="to-remove-a-service-reference"></a>Hizmet başvurusunu kaldırmak için

-   İçinde **Çözüm Gezgini**, hizmet başvurusunu sağ tıklayın ve ardından **Sil**.

     Hizmet istemcisi çözümden kaldırılacak ve hizmeti tanımlayan meta veriler kaldırılacak *app.config* dosya.

    > [!NOTE]
    >  Hizmet başvuru yapan tüm kodları el ile kaldırılması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)