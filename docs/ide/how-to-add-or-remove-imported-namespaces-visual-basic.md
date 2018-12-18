---
title: 'Nasıl yapılır: ekleme veya kaldırma içeri aktarılan ad alanlarını (Visual Basic)'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df39b7867cd4c7baa2206b2c63634810b2f29dde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944654"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Nasıl yapılır: ekleme veya kaldırma içeri aktarılan ad alanlarını (Visual Basic)

Bir ad alanı içe aktarma öğesi tam olarak niteleme olmadan bu ad alanındaki öğeler kodunuzda kullanmanıza olanak sağlar. Erişmek istiyorsanız, örneğin, `Create` yönteminde `System.Messaging.MessageQueue` alabileceğiniz sınıfı, `System.Messaging` ad alanı ve yalnızca gereksinim duyduğunuz kodda öğesine başvuruda `MessageQueue.Create`.

 İçeri aktarılan ad alanları üzerindeki yönetilen **başvuruları** sayfasında **Proje Tasarımcısı**. Bu iletişim kutusunda belirttiğiniz içeri aktarmalar doğrudan derleyiciye geçirilir (*/Imports*) ve projenizdeki tüm dosyalara uygulayabilirsiniz. Kullanmak `Imports` deyimi bir tek kaynak kodu dosyasına bir ad kullanın.

### <a name="to-add-an-imported-namespace"></a>İçeri aktarılan ad eklemek için

1.  İçinde **Çözüm Gezgini**, çift **My proje** projesi için düğüm.

2.  İçinde **Proje Tasarımcısı**, tıklatın **başvuruları** sekmesi.

3.  İçinde **içeri aktarılan ad alanları** listesinde, eklemek istediğiniz ad alanı için onay kutusunu seçin.

    > [!NOTE]
    >  Alınmak için ad alanı başvurulan bir bileşenin olması gerekir. Ad alanı listede görünmüyorsa, içerdiği bileşenine bir başvuru eklemeniz gerekir. Daha fazla bilgi için bkz: [bir projedeki başvuruları yönetme](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>İçeri aktarılan ad alanını kaldırmak için

1.  İçinde **Çözüm Gezgini**, çift **My proje** projesi için düğüm.

2.  İçinde **Proje Tasarımcısı**, tıklatın **başvuruları** sekmesi.

3.  İçinde **içeri aktarılan ad alanları** listesinde, kaldırmak istediğiniz ad alanı için onay kutusunu temizleyin.

## <a name="user-imports"></a>Kullanıcı içeri aktarmalar
 Kullanıcı içeri aktarmalar, belirli bir sınıfın tüm ad alanı yerine bir ad alanı içinde almaya izin verir. Örneğin, uygulamanız için alma olabilir <xref:System.Diagnostics> ad alanı, ancak ilgilendiğiniz bu ad alanındaki tek sınıf `Debug` sınıfı. Tanımlayabileceğiniz <xref:System.Diagnostics.Debug> bir kullanıcı olarak içeri aktarma ve alma için Kaldır'ı <xref:System.Diagnostics>.

 Daha sonra fikir değiştirirseniz ve yalnızca karar verirseniz, gerçekten `EventLog` girin, gerekli sınıfı, <xref:System.Diagnostics.EventLog> bir kullanıcı olarak alma ve üzerine yazma <xref:System.Diagnostics.Debug> güncelleştirme işlevini kullanarak.

### <a name="to-add-a-user-import"></a>Bir kullanıcı alma eklemek için

1.  İçinde **Çözüm Gezgini**, çift **My proje** projesi için düğüm.

2.  İçinde **Proje Tasarımcısı**, tıklatın **başvuruları** sekmesi.

3.  Aşağıdaki metin kutusundaki **içeri aktarılan ad alanları** listesinde, kök ad alanı dahil almak istediğiniz ad alanı için tam bir ad girin.

4.  Tıklatın **kullanıcı alma ekleme** ad alanına eklemek için düğmeyi **içeri aktarılan ad alanları** listesi.

    > [!NOTE]
    > **Kullanıcı alma ekleme** düğmesi devre dışı bırakılacak ad alanı zaten listeden birini eşleşirse; bir alma işlemi iki kez eklenemiyor.

### <a name="to-update-a-user-import"></a>Bir kullanıcı alma güncelleştirmek için

1.  İçinde **Çözüm Gezgini**, çift **My proje** projesi için düğüm.

2.  İçinde **Proje Tasarımcısı**, tıklatın **başvuruları** sekmesi.

3.  İçinde **içeri aktarılan ad alanları** listesinde, değiştirmek istediğiniz ad alanını seçin.

4.  Aşağıdaki metin kutusundaki **içeri aktarılan ad alanları** listesinde, yeni ad alanı için bir ad girin.

5.  Tıklatın **güncelleştirme kullanıcı alma** ad alanını güncelleştirmek için düğmesini **içeri aktarılan ad alanları** listesi.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)