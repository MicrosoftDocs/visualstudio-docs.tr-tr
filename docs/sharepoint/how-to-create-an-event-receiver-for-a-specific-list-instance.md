---
title: 'Nasıl yapılır: belirli bir liste örneği için olay alıcısı oluşturma | Microsoft Docs'
titleSuffix: ''
description: Belirli bir liste örneği için olay alıcısı oluşturun. Liste örneği olay alıcısı, bir liste tanımının herhangi bir örneğinde oluşan olaylara yanıt verir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 664a7ac4e763b2378cf30603c417aacde27c2e47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925495"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Nasıl yapılır: belirli bir liste örneği için olay alıcısı oluşturma
  Liste örneği olay alıcısı, bir liste tanımının herhangi bir örneğinde oluşan olaylara yanıt verir. Olay alıcısı şablonu belirli bir liste örneğinin hedeflemesini etkinleştirmese de, belirli bir liste örneğindeki olaylara yanıt vermek için liste tanımı kapsamındaki bir olay alıcısını değiştirebilirsiniz.

 Belirli bir liste örneğini hedeflemek için, olay alıcısı için *Elements.xml* `ListTemplateId` ile değiştirin `ListUrl` ve liste örneğinin URL 'sini ekleyin.

## <a name="create-a-list-instance-event-receiver"></a>Liste örneği olay alıcısı oluşturma
 Aşağıdaki adımlarda, bir liste öğesi olay alıcısının yalnızca özel Duyurular-liste örneğinde gerçekleşen olaylara yanıt verecek şekilde nasıl değiştirileceği gösterilmektedir.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Bir olay alıcısını belirli bir liste örneğine yanıt verecek şekilde değiştirmek için

1. Bir tarayıcıda, SharePoint sitesini açın.

2. Gezinti bölmesinde, bağlantısını **listeler** .

3. **Tüm site içeriği** sayfasında **Oluştur** bağlantısını seçin.

4. **Oluştur** Iletişim kutusunda **Duyurular** türünü seçin **, duyuruyu duyurun ve ardından** **Oluştur** düğmesini seçin.

5. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir olay alıcısı projesi oluşturun.

6. **Ne tür bir olay alıcısı istiyorsunuz?** listesinde, **liste öğesi olayları**' nı seçin.

    > [!NOTE]
    > Ayrıca, bir liste tanımına kapsamlar olan diğer tür bir olay alıcıyı seçebilirsiniz (örneğin, **e-posta olaylarını listeleme** veya **Iş akışı olaylarını listeleme**).

7. **Hangi öğe olay kaynağı olmalıdır?** listesinde, **Duyurular**' ı seçin.

8. **Aşağıdaki olayları işle** listesinde, **bir öğe ekleniyor** onay kutusunu seçin ve ardından **son** düğmesini seçin.

9. **Çözüm Gezgini**' de, EventReceiver1 altında *Elements.xml* açın.

     Olay alıcısı Şu anda aşağıdaki satırı kullanarak Duyurular listesi tanımına başvuruyor:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Bu satırı aşağıdaki metinle değiştirin:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Bu, olay alıcısının yalnızca yeni oluşturduğunuz **Testannounte** bildirimleri listesinde gerçekleşen olaylara yanıt vermesini sağlar. `ListURL`Özniteliğini, SharePoint sunucusundaki herhangi bir liste örneğine başvuracak şekilde değiştirebilirsiniz.

10. Olay alıcısı için kod dosyasını açın ve ımadding yöntemine bir kesme noktası koyun.

11. Çözümü derlemek ve çalıştırmak için **F5** tuşunu seçin.

12. SharePoint 'te, gezinti bölmesinde **Testannounte** bağlantısı ' nı seçin.

13. **Yeni duyuru ekle** bağlantısını seçin.

14. Duyuru için bir başlık girin ve **Kaydet** düğmesini seçin.

     Yeni öğe özel Duyurular listesine eklendiğinde kesme noktasının isabet ettiğini unutmayın.

15. Sürdürülecek **F5** tuşunu seçin.

16. Gezinti bölmesinde, **listeler** bağlantısını seçin ve ardından **Duyurular** bağlantısını seçin.

17. Yeni bir duyuru ekleyin.

     Alıcı yalnızca özel duyuru listesi örneğindeki etkinliklere yanıt verecek şekilde yapılandırıldığı için, yeni **duyuruda olay** alıcısının tetiklemez olduğuna dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
