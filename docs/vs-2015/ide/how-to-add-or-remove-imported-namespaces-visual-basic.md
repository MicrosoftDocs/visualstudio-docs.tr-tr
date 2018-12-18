---
title: 'Nasıl yapılır: ekleme veya kaldırma (Visual Basic) içeri aktarılan ad uzaylarını | Microsoft Docs'
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
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 730ebcf8029abf51e6cb04c74b826593139cfdc5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196410"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Nasıl Yapılır: İçeri Aktarılan Ad Uzaylarını Ekleme veya Kaldırma (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir ad alanı içeri aktarma öğesi tam olarak niteleme olmadan kodunuzda bu ad alanından öğeler kullanmanıza olanak tanır. Örneğin erişmek istiyorsanız, `Create` yönteminde `System.Messaging.MessageQueue` alabileceğiniz sınıfı `System.Messaging` ad alanı ve yalnızca gereksinim duyduğunuz kod öğesi bakın `MessageQueue.Create`.  
  
 İçeri aktarılan ad uzaylarını yönetilir **başvuruları** sayfasının **Proje Tasarımcısı**. Bu iletişim kutusunda belirttiğiniz Imports doğrudan derleyici geçirilen (`/imports`) ve projenizdeki tüm dosyalara uygulayın. Kullanma `Imports` tek kaynak kod dosyasında bir ad alanını kullanacak şekilde deyimi.  
  
### <a name="to-add-an-imported-namespace"></a>Bir içeri aktarılan ad alanı eklemek için  
  
1.  İçinde **Çözüm Gezgini**, çift **Projem** projesinin düğümü.  
  
2.  İçinde **Proje Tasarımcısı**, tıklayın **başvuruları** sekmesi.  
  
3.  İçinde **içeri aktarılan ad alanlarını** listesinde, eklemek istediğiniz ad alanı için onay kutusunu seçin.  
  
    > [!NOTE]
    >  Ad alanı içeri aktarılması için başvurulan bir bileşen olarak olması gerekir. Ad alanı listede görünmüyorsa, içerdiği bileşenine bir başvuru eklemeniz gerekir. Daha fazla bilgi için [nasıl NIB: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
### <a name="to-remove-an-imported-namespace"></a>Bir içeri aktarılan ad alanı kaldırmak için  
  
1.  İçinde **Çözüm Gezgini**, çift **Projem** projesinin düğümü.  
  
2.  İçinde **Proje Tasarımcısı**, tıklayın **başvuruları** sekmesi.  
  
3.  İçinde **içeri aktarılan ad alanlarını** listesinde, kaldırmak istediğiniz ad alanı için onay kutusunu temizleyin.  
  
## <a name="user-imports"></a>Kullanıcı içeri aktarmalar  
 Kullanıcı içeri aktarmalar, belirli bir sınıf içindeki tüm ad alanı yerine bir ad alanı içe olanak tanır. Örneğin, uygulamanızın yönelik içeri aktarma olabilir `Systems.Diagnostics` ad alanı, ancak yalnızca sınıf ilgilendiğiniz bu ad alanı içinde `Debug` sınıfı. Tanımlayabileceğiniz `System.Diagnostics.Debug` bir kullanıcı olarak içeri aktarma ve içeri aktarma için Kaldır'ı `System.Diagnostics`.  
  
 Daha sonra değiştirmeleri ve yalnızca karar verirseniz gerçekten `EventLog` gereksinim sınıfı yazabilirsiniz `System.Diagnostics.EventLog` bir kullanıcı olarak içeri aktarma ve üzerine `System.Diagnostics.Debug` güncelleştirme işlevini kullanarak.  
  
#### <a name="to-add-a-user-import"></a>Kullanıcı içeri aktarma eklemek için  
  
1.  İçinde **Çözüm Gezgini**, çift **Projem** projesinin düğümü.  
  
2.  İçinde **Proje Tasarımcısı**, tıklayın **başvuruları** sekmesi.  
  
3.  Metin kutusundaki **içeri aktarılan ad alanlarını** listesinde, almak istediğiniz ad alanı için tam adı kök ad alanı dahil girin.  
  
4.  Tıklayın **kullanıcı içeri aktarma eklemek** ad alanına eklemek için Ekle düğmesine **içeri aktarılan ad alanlarını** listesi.  
  
    > [!NOTE]
    >  **Kullanıcı içeri aktarma eklemek** düğmesini devre dışı bırakılacak ad alanı zaten listede bir eşleşiyorsa; bir alma işlemi iki kez ekleyemezsiniz.  
  
#### <a name="to-update-a-user-import"></a>Kullanıcı içeri aktarma güncelleştirmek için  
  
1.  İçinde **Çözüm Gezgini**, çift **Projem** projesinin düğümü.  
  
2.  İçinde **Proje Tasarımcısı**, tıklayın **başvuruları** sekmesi.  
  
3.  İçinde **içeri aktarılan ad alanlarını** listesinde, değiştirmek istediğiniz ad alanını seçin.  
  
4.  Metin kutusundaki **içeri aktarılan ad alanlarını** listesinde, yeni ad alanı için bir ad girin.  
  
5.  Tıklayın **güncelleştirme kullanıcı içeri aktarma** ad alanında güncelleştirmek için düğmesini **içeri aktarılan ad alanlarını** listesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)



