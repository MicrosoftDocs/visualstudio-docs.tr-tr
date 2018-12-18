---
title: 'Nasıl yapılır: bir hizmetteki verilere bağlanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce851a864dd11759c36c7ae6cb275e9e71cd11a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301801"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Nasıl yapılır: Bir Hizmetteki Verilere Bağlanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Uygulamanızı çalıştırarak bir hizmetten döndürülen veri bağlama [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) seçerek **hizmet** üzerinde **verikaynağıtürüseçin**sayfası.  
  
 Sihirbaz tamamlandıktan sonra bir hizmet başvurusu projenize eklenir ve hemen kullanılabilir [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Görünen öğeler **veri kaynakları** penceresinde bağımlı hizmetin döndürdüğü bilgileri bulunur. Bazı hizmetler için yeterli bilgi sağlamayabilir **veri kaynağı Yapılandırma Sihirbazı** bağlanabilir nesneleri oluşturmak için. Hizmet yazılmamış bir veri kümesi döndürürse, örneğin, daha sonra hiçbir öğe görünür **veri kaynakları penceresi** sihirbaz. Yazılmayan veri kümeleri, şema sağlamaz, bu nedenle sihirbazın veri kaynağını oluşturmak için yeterli bilgi yok olmasıdır.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Uygulamanız bir hizmete bağlanmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **yeni veri kaynağı Ekle**.  
  
2.  Seçin **hizmet** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
3.  İstediğiniz kullanın veya hizmeti adresini girmek **bulma** geçerli çözümde hizmeti bulun ve ardından **Git**.  
  
4.  İsteğe bağlı olarak, yeni **Namespace** yerine varsayılan değer türü belirtilmiş olmalıdır.  
  
    > [!NOTE]
    >  Tıklayın **Gelişmiş** açmak için [hizmeti başvuru iletişim kutusunu](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Tıklayın **Tamam** projenize bir hizmet başvurusu eklemek için.  
  
6.  **Son**'a tıklayın.  
  
     Veri kaynağı eklenir **veri kaynakları** penceresi.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
#### <a name="to-add-functionality-to-your-application"></a>Uygulamanıza işlev eklemek için  
  
-   Bir öğe seçin **veri kaynakları** penceresi ve ilişkili denetimler oluşturmak için bir form üzerine sürükleyin. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir WCF veri hizmetine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

