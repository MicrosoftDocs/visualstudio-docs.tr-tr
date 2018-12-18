---
title: 'Nasıl yapılır: Bir Hizmetteki Verilere Bağlanma'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f8f7371418df19ec8452334641c7c9414328e557
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305019"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Nasıl yapılır: bir hizmetteki verilere bağlanma

Uygulamanızı çalıştırarak bir hizmetten döndürülen veri bağlama [veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png) seçerek **hizmet** üzerinde **verikaynağıtürüseçin**sayfası.

Sihirbaz tamamlandıktan sonra bir hizmet başvurusu projenize eklenir ve hemen kullanılabilir [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Görünen öğeler **veri kaynakları** penceresinde bağımlı hizmetin döndürdüğü bilgileri bulunur. Bazı hizmetler için yeterli bilgi sağlamayabilir **veri kaynağı Yapılandırma Sihirbazı** bağlanabilir nesneleri oluşturmak için. Hizmet yazılmamış bir veri kümesi döndürürse, örneğin, hiçbir öğe görünür **veri kaynakları** sihirbaz penceresi. Yazılmayan veri kümeleri, şema sağlamaz, bu nedenle sihirbazın veri kaynağını oluşturmak için yeterli bilgi yok olmasıdır.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Uygulamanız bir hizmete bağlanmak için

1.  Üzerinde **veri** menüsünü tıklatın **yeni veri kaynağı Ekle**.

2.  Seçin **hizmet** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

3.  İstediğiniz kullanın veya hizmeti adresini girmek **bulma** geçerli çözümde hizmeti bulun ve ardından **Git**.

4.  İsteğe bağlı olarak, yeni bir yazabilirsiniz **Namespace** varsayılan değer yerine.

    > [!NOTE]
    > Tıklayın **Gelişmiş** açmak için [hizmet başvurusu Yapılandır iletişim kutusu](../data-tools/configure-service-reference-dialog-box.md).

5.  Tıklayın **Tamam** projenize bir hizmet başvurusu eklemek için.

6.  **Son**'a tıklayın.

     Veri kaynağı eklenir **veri kaynakları** penceresi.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanıza işlevsellik eklemek için bir öğe seçin. **veri kaynakları** penceresi ve ilişkili denetimler oluşturmak için bir form üzerine sürükleyin. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bir WCF veri hizmetine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)