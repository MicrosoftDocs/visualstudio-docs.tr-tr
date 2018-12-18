---
title: 'Nasıl yapılır: ekleme, güncelleştirme veya bir WCF veri hizmeti başvurusunu Kaldır | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b14a83b195809dff89fa89bb6fcf91050e2f8a0c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192263"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Nasıl Yapılır: WCF Veri Hizmeti Başvurusunu Güncelleme veya Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
A *hizmet başvurusu* bir projeye bir veya daha fazla erişim sağlayan [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]. Kullanım **hizmet Başvurusu Ekle** aramak için iletişim kutusu [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] geçerli çözümde, yerel olarak bir yerel ağ veya Internet üzerinde.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>Hizmet başvurusu ekleme  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Bir dış hizmet için bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, hizmete ekleyin ve ardından istediğiniz proje adına sağ tıklayın **hizmet Başvurusu Ekle**.  
  
     **Hizmet Başvurusu Ekle** iletişim kutusu görüntülenir.  
  
2.  İçinde **adresi** kutusuna hizmeti için URL girin ve ardından **Git** hizmet için aranacak. Hizmet kullanıcı adı ve parola güvenlik uygularsa, bir kullanıcı adı ve parolası istenebilir.  
  
    > [!NOTE]
    >  Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır. Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.  
  
     URL'den belirleyebilirsiniz **adresi** listesinde, geçerli hizmet meta verileri bulundu önceki 15 URL depolar.  
  
     Arama yapılırken bir ilerleme çubuğu görüntülenir. Tıklayarak arama dilediğiniz zaman durdurabilirsiniz **Durdur**.  
  
3.  İçinde **Hizmetleri** listesinde, bir varlık kümesi seçin ve istediğiniz hizmeti düğümünü genişletin.  
  
4.  İçinde **Namespace** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.  
  
5.  Tıklayın **Tamam** projesine başvuru eklenemiyor.  
  
     Bir hizmeti istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta verileri app.config dosyasına eklenir.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Geçerli çözümde bir hizmet başvurusu eklemek için  
  
1.  İçinde **Çözüm Gezgini**, hizmete ekleyin ve ardından istediğiniz proje adına sağ tıklayın **hizmet Başvurusu Ekle**.  
  
     **Hizmet Başvurusu Ekle** iletişim kutusu görüntülenir.  
  
2.  Tıklayın **Bul**.  
  
     Tüm hizmetler (her ikisi de [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] ve WCF hizmetleri) geçerli çözümde eklenen **Hizmetleri** listesi.  
  
3.  İçinde **Hizmetleri** listesinde, bir varlık kümesi seçin ve istediğiniz hizmeti düğümünü genişletin.  
  
4.  İçinde **Namespace** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.  
  
5.  Tıklayın **Tamam** projesine başvuru eklenemiyor.  
  
     Bir hizmeti istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta verileri app.config dosyasına eklenir.  
  
## <a name="updating-a-service-reference"></a>Bir hizmet başvurusu güncelleştiriliyor  
 Varlık veri modeli için bir [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] bazen değişir. Bu durumda, hizmet başvurusunu güncelleştirilmesi gerekir.  
  
#### <a name="to-update-a-service-reference"></a>Bir hizmet başvurusu güncelleştirilecek  
  
-   İçinde **Çözüm Gezgini**, hizmet başvurusunu sağ tıklayın ve ardından **güncelleştirme hizmet başvurusu**.  
  
     İlerleme durumu iletişim kutusu, başvuru özgün konumundan güncelleştirilir ve hizmeti istemcisi meta verilerindeki değişiklikleri yansıtacak şekilde yeniden görüntülenir.  
  
## <a name="removing-a-service-reference"></a>Bir hizmet başvurusu kaldırılıyor  
 Bir hizmet başvurusu artık kullanılıyorsa çözümünüzden kaldırabilirsiniz.  
  
#### <a name="to-remove-a-service-reference"></a>Hizmet başvurusunu kaldırmak için  
  
-   İçinde **Çözüm Gezgini**, hizmet başvurusunu sağ tıklayın ve ardından **Sil**.  
  
     Hizmet istemcisi çözümden kaldırılır ve hizmeti tanımlayan meta verileri app.config dosyasından kaldırılır.  
  
    > [!NOTE]
    >  Hizmet başvuru yapan tüm kodları el ile kaldırılması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

