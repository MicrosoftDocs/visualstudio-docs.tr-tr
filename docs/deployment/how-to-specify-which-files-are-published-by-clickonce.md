---
title: 'Nasıl yapılır: ClickOnce tarafından hangi dosyaların yayımlandığını belirtme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: efe2e5ab9f2074c1706f14ac52f655921af4b9a2
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080470"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Nasıl yapılır: ClickOnce tarafından hangi dosyaların yayımlandığını belirtme
Yayımlama sırasında bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projedeki uygulama, tüm kod dışı dosyalara yanı sıra uygulama dağıtılır. Bazı durumlarda değil istediğiniz veya belirli dosyaları yayımlamanız gerekir veya koşullara göre belirli dosyaları yüklemek isteyebilirsiniz. Visual Studio dosyaları dışarıda bırak, dosyalar, veri dosyalarını veya önkoşul olarak işaretleme ve koşullu yüklemek için dosya grupları oluşturmak için özellikler sunar.  
  
 Dosyaları bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama yönetilen **uygulama dosyaları** iletişim kutusu, erişilebilir **Yayımla** sayfasının **Proje Tasarımcısı**.  
  
 Başlangıçta, adlı tek bir dosya grubu var. **(gerekli)**. Ek dosya grupları oluşturun ve dosyalarını atayabilirsiniz. Değiştiremezsiniz **indirme grubu** uygulamayı çalıştırmak gerekli olan dosyalar için. Örneğin, uygulamanın .exe veya dosyaları veri dosyalarını ait olarak işaretledi **(gerekli)** grubu.  
  
 Yayımlama durumu varsayılan bir dosyanın değeri ile etiketlenir **(otomatik)**. Örneğin, uygulamanın .exe yayımla durumuna sahip **Ekle (otomatik)** varsayılan olarak.  
  
 İle dosyaları **derleme eylemi** özelliğini **içerik** uygulama dosyaları belirlenmiştir ve varsayılan olarak dahil olarak işaretlenir. Bunlar eklenebilen, hariç veya veri dosyaları olarak işaretlenmiş. Özel durumlar aşağıdaki gibidir:  
  
-   SQL veritabanı gibi veri dosyaları (*.mdf* ve *.mdb*) dosyalarını ve XML dosyalarını işaretlenir veri dosyaları olarak varsayılan olarak.  
  
-   Derlemelere başvuruları (*.dll* dosyaları) başvuru eklediğinizde, aşağıdaki gibi belirlenmiştir: varsa **Yereli Kopyala** olduğu **False**, varsayılan olarak bir önkoşul olarak işaretlenmiş derleme (**önkoşul (otomatik)**), bulunmalıdır GAC'de uygulama yüklenmeden önce. Varsa **Yereli Kopyala** olduğu **True**, derleme varsayılan olarak bir uygulama derleme olarak işaretlenir (**Ekle (otomatik)**) ve yükleme sırasında uygulama klasörüne kopyalanır. Bir COM başvurusu görünür **uygulama dosyaları** iletişim kutusu (olarak bir *.ocx* dosyası) yalnızca kendi **yalıtılmış** özelliği **True**. Varsayılan olarak dahil edilir.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Uygulama dosyaları iletişim kutusuna dosya eklemek için  
  
1.  Bir veri dosyasını seçin **Çözüm Gezgini**.  
  
2.  Özellikler penceresinde değişiklik **derleme eylemi** özelliğini **içerik** değeri.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>ClickOnce yayımlama dosyaları hariç tutmak için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **uygulama dosyaları** açmak için düğmeyi **uygulama dosyaları** iletişim kutusu.  
  
4.  İçinde **uygulama dosyaları** iletişim kutusunda, çıkarmak istediğiniz dosyayı seçin.  
  
5.  İçinde **yayımlama durumu** alanın, Seç **hariç** aşağı açılan listeden.  
  
### <a name="to-mark-files-as-data-files"></a>Dosyaları veri dosyaları olarak işaretlemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **uygulama dosyaları** açmak için düğmeyi **uygulama dosyaları** iletişim kutusu.  
  
4.  İçinde **uygulama dosyaları** iletişim kutusunda, dışlamak istediğiniz dosyayı seçin.  
  
5.  İçinde **yayımlama durumu** alanın, Seç **veri dosyası** aşağı açılan listeden.  
  
### <a name="to-mark-files-as-prerequisites"></a>Dosyaları önkoşul olarak işaretlemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **uygulama dosyaları** açmak için düğmeyi **uygulama dosyaları** iletişim kutusu.  
  
4.  İçinde **uygulama dosyaları** iletişim kutusunda, uygulama derlemeyi seçin (*.dll* dosyası) bir önkoşul olarak işaretlemek istediğiniz. Uygulamanızı uygulama derlemesine bir başvuru listesinde görünmesi için sırayla sahip olmaları gerektiğini unutmayın.  
  
5.  İçinde **yayımlama durumu** alanın, Seç **önkoşul** aşağı açılan listeden.  
  
### <a name="to-add-a-new-file-group"></a>Yeni bir dosya grubu eklemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **uygulama dosyaları** açmak için düğmeyi **uygulama dosyaları** iletişim kutusu.  
  
4.  İçinde **uygulama dosyaları** iletişim kutusunda **grubu** yeni gruba dahil etmek istediğiniz bir dosya için alan.  
  
    > [!NOTE]
    >  Dosyaları olmalıdır **derleme eylemi** özelliğini **içerik** dosya adlarını görünmesi **uygulama dosyaları** iletişim kutusu.  
  
5.  İçinde **indirme grubu** alanın, Seç  **\<yeni … >** aşağı açılan listeden.  
  
6.  İçinde **yeni grup** iletişim kutusunda grup için bir ad girin ve ardından **Tamam**.  
  
### <a name="to-add-a-file-to-a-group"></a>Bir dosya grubuna eklemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **uygulama dosyaları** açmak için düğmeyi **uygulama dosyaları** iletişim kutusu.  
  
4.  İçinde **uygulama dosyaları** iletişim kutusunda **grubu** yeni gruba dahil etmek istediğiniz bir dosya için alan.  
  
5.  İçinde **indirme grubu** alanında, aşağı açılan listeden bir grubu seçin.  
  
    > [!NOTE]
    >  Değiştiremezsiniz **indirme grubu** uygulamayı çalıştırmak gerekli olan dosyalar için.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)