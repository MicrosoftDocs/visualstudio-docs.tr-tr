---
title: 'Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 890a61290d7606fb2a03ea7aed2c4782e5b69b67
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388869"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama
Bir ClickOnce uygulamasını kullanıcılar tarafından kullanılabilmesi için bir dosya paylaşımı veya yolu, FTP sunucusu veya çıkarılabilir medya yayımlamanız gerekir. Uygulama Yayımlama Sihirbazı'nı kullanarak yayınlayabilirsiniz; yayımlama ile ilgili ek özellikler kullanılabilir **Yayımla** sayfasının **Proje Tasarımcısı**. Daha fazla bilgi için [yayımlama ClickOnce uygulamaları](../deployment/publishing-clickonce-applications.md).

Yayımlama Sihirbazı'nı çalıştırmadan önce yayınlama özelliklerini uygun şekilde ayarlamanız gerekir. ClickOnce uygulamanızı imzalamak için bir anahtar belirlemek istiyorsanız, örneğin, vb. yapabileceğiniz **imzalama** sayfasının **Proje Tasarımcısı**. Daha fazla bilgi için [güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> ClickOnce kullanarak bir uygulamanın birden fazla sürüm yüklediğinizde, yükleme uygulamanın önceki sürümlerini adlı bir klasöre taşır. *arşiv*, belirttiğiniz yayımla konumunda. Yükleme dizini temizler önceki sürümünden önceki sürümleri bu şekilde korur arşivleme.

> [!NOTE]
> İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [ayarlarına](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>Bir dosya paylaşımı ya da yolu yayımlamak için

1. İçinde **Çözüm Gezgini**, uygulama projesini seçin.

2. Üzerinde **derleme** menüsünde tıklatın **Yayımla** *Projectname*.

    Yayınla Sihirbazı görüntülenir.

3. İçinde **nerede uygulamayı yayımlamak istiyorsunuz?** sayfasında, geçerli bir FTP sunucusu adresi ya da gösterilen biçimlerden birini kullanarak geçerli dosya yolu girin ve ardından **sonraki**.

4. İçinde **nasıl kullanıcılar uygulamayı yükleyecek?** sayfasında, kullanıcıların nereye uygulamayı yüklemek için konumu seçin:

   -   Kullanıcılar Web sitesinden yükleyecekse tıklayın **Web sitesinden** ve önceki adımda girilen dosya yoluna karşılık gelen URL'yi girin. **İleri**'ye tıklayın. (Yayımlama konumu olarak bir FTP adresi belirttiğinizde bu seçenek genellikle kullanılır. FTP üzerinden doğrudan indirme desteklenmiyor. Bu nedenle, bir URL girmeniz gerekir.)

   -   Kullanıcılar, uygulamayı doğrudan dosya paylaşımından yükleyecekse tıklayın **UNC yolu veya dosya paylaşımı**ve ardından **sonraki**. (Bu formun konumlarını yayımlamak için *c:\deploy\myapp* veya  *\\\server\myapp*.)

   -   Kullanıcılar çıkarılabilir medyadan yükleyecekse tıklayın **CD-ROM veya DVD-ROM**ve ardından **sonraki**.

5. Üzerinde **uygulama çevrimdışı kullanılabilir mi?** sayfasında, uygun seçeneği tıklayın:

   - Çalıştırılacak uygulamanın etkinleştirmek istiyorsanız, kullanıcı bağlantısı kesilmiş ağdan, tıklayın **Evet, bu uygulama çevrimiçi veya çevrimdışı kullanılabilir mi**. Bir kısayol **Başlat** menüsünde uygulama için oluşturulur.

   - Uygulamayı doğrudan yayınlama konumundan çalıştırmak isterseniz **Hayır, bu uygulama yalnızca çevrimiçi kullanılabilir**. Bir kısayol **Başlat** menü oluşturulmayacak.

     Devam etmek için **İleri** 'ye tıklayın.

6. Tıklayın **son** uygulamayı yayınlamak için.

    Yayımlama durumu, durum bildirim alanında görüntülenir.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Bir CD-ROM veya DVD-ROM yayımlamak için

1. İçinde **Çözüm Gezgini**, uygulama projesine sağ tıklayıp **özellikleri**.

    **Proje Tasarımcısı** görünür.

2. Tıklayın **Yayımla** açmak için sekmesinde **Yayımla** sayfasını **Proje Tasarımcısı**, tıklatıp **Yayımlama Sihirbazı** düğmesi.

    Yayınla Sihirbazı görüntülenir.

3. İçinde **nerede uygulamayı yayımlamak istiyorsunuz?** sayfasında, dosya yolunu veya FTP konumu burada uygulama yayımlanacak, örneğin girin *d:\deploy*. Ardından **sonraki** devam etmek için.

4. Üzerinde **nasıl kullanıcılar uygulamayı yükleyecek?** sayfasında, gelen bir **CD-ROM veya DVD-ROM**ve ardından **sonraki**.

   > [!NOTE]
   >  Yüklemenin otomatik olarak çalışmasını istiyorsanız, CD-ROM'dan eklenir sürücüsüne açık **Yayımla** sayfasını **Proje Tasarımcısı** tıklatıp **seçenekleri** düğmesini ve ardından **yayımlama seçeneği** seçin **için CD yüklemeleri, CD takıldığında Kurulumu otomatik olarak Başlat**.

5. Uygulamanızı CD-ROM üzerinde dağıtırsanız, güncelleştirmeleri bir Web sitesinden sağlamak isteyebilirsiniz. İçinde **burada Uygulama Güncelleştirmeleri denetle?** sayfasında, güncelleştirme bir seçeneği belirleyin:

   - Uygulama güncelleştirmeleri denetleyecekse, tıklayın **uygulama aşağıdaki konumdan güncelleştirmelerini denetleyecek** ve burada güncelleştirmeleri denetleyecekse konumu girin. Bu, bir dosya konumu, Web sitesi veya FTP sunucusu olabilir.

   - Uygulama güncelleştirmeleri denetlemeyecekse, tıklayın **uygulama güncelleştirmeleri denetlemeyecek**.

     Devam etmek için **İleri** 'ye tıklayın.

6. Tıklayın **son** uygulamayı yayınlamak için.

    Yayımlama durumu, durum bildirim alanında görüntülenir.

   > [!NOTE]
   >  Yayınlama tamamlandıktan sonra CD-ROM veya DVD-ROM medyaya dosyaları belirttiğiniz konuma kopyalamak için DVD-Rewriter adım 3 ya da CD-Rewriter kullanmanız gerekecektir.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)
- [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)