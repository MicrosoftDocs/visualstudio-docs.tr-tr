---
title: 'Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f8708658e5daf90e24a0336040ba2b766d5ae975
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862833"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir ClickOnce uygulamasını kullanıcılar tarafından kullanılabilmesi için bir dosya paylaşımı veya yolu, FTP sunucusu veya çıkarılabilir medya yayımlamanız gerekir. Uygulama Yayımlama Sihirbazı'nı kullanarak yayınlayabilirsiniz; yayımlama ile ilgili ek özellikler kullanılabilir **Yayımla** sayfasının **Proje Tasarımcısı**. Daha fazla bilgi için [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md).  
  
 Yayımlama Sihirbazı'nı çalıştırmadan önce yayınlama özelliklerini uygun şekilde ayarlamanız gerekir. ClickOnce uygulamanızı imzalamak için bir anahtar belirlemek istiyorsanız, örneğin, vb. yapabileceğiniz **imzalama** sayfasının **Proje Tasarımcısı**. Daha fazla bilgi için [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  ClickOnce kullanarak bir uygulamanın birden fazla sürüm yüklediğinizde, yükleme uygulamanın önceki sürümlerini belirttiğiniz yayımlama konum arşivinde adlı bir klasöre taşır. Yükleme dizini temizler önceki sürümünden önceki sürümleri bu şekilde korur arşivleme.  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Bir dosya paylaşımı ya da yolu yayımlamak için  
  
1. İçinde **Çözüm Gezgini**, uygulama projesini seçin.  
  
2. Üzerinde **derleme** menüsünde tıklatın **Yayımla**`Projectname`.  
  
    Yayınla Sihirbazı görüntülenir.  
  
3. İçinde **nerede uygulamayı yayımlamak istiyorsunuz?** sayfasında, geçerli bir FTP sunucusu adresi ya da gösterilen biçimlerden birini kullanarak geçerli dosya yolu girin ve ardından **sonraki**.  
  
4. İçinde **nasıl kullanıcılar uygulamayı yükleyecek?** sayfasında, kullanıcıların nereye uygulamayı yüklemek için konumu seçin:  
  
   -   Kullanıcılar Web sitesinden yükleyecekse tıklayın **Web sitesinden** ve önceki adımda girilen dosya yoluna karşılık gelen URL'yi girin. **İleri**'ye tıklayın. (Yayımlama konumu olarak bir FTP adresi belirttiğinizde bu seçenek genellikle kullanılır. FTP üzerinden doğrudan indirme desteklenmiyor. Bu nedenle, bir URL girmeniz gerekir.)  
  
   -   Kullanıcılar, uygulamayı doğrudan dosya paylaşımından yükleyecekse tıklayın **UNC yolu veya dosya paylaşımı**ve ardından **sonraki**. (Bu form c:\deploy\myapp konumlarını yayımlamak için veya \\\server\myapp.)  
  
   -   Kullanıcılar çıkarılabilir medyadan yükleyecekse tıklayın **CD-ROM veya DVD-ROM**ve ardından **sonraki**.  
  
5. Üzerinde **uygulama çevrimdışı kullanılabilir mi?** sayfasında, uygun seçeneği tıklayın:  
  
   - Çalıştırılacak uygulamanın etkinleştirmek istiyorsanız, kullanıcı bağlantısı kesilmiş ağdan, tıklayın **Evet, bu uygulama çevrimiçi veya çevrimdışı kullanılabilir mi**. Bir kısayol **Başlat** menüsünde uygulama için oluşturulur.  
  
   - Uygulamayı doğrudan yayınlama konumundan çalıştırmak isterseniz **Hayır, bu uygulama yalnızca çevrimiçi kullanılabilir**. Bir kısayol **Başlat** menü oluşturulmayacak.  
  
     Devam etmek için **İleri** 'ye tıklayın.  
  
6. Tıklayın **son** uygulamayı yayınlamak için.  
  
    Yayımlama durumu, durum bildirim alanında görüntülenir.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Bir CD-ROM veya DVD-ROM yayımlamak için  
  
1. İçinde **Çözüm Gezgini**, uygulama projesine sağ tıklayıp **özellikleri**.  
  
    **Proje Tasarımcısı** görünür.  
  
2. Tıklayın **Yayımla** açmak için sekmesinde **Yayımla** sayfasını **Proje Tasarımcısı**, tıklatıp **Yayımlama Sihirbazı** düğmesi.  
  
    Yayınla Sihirbazı görüntülenir.  
  
3. İçinde **nerede uygulamayı yayımlamak istiyorsunuz?** sayfasında, dosya yolunu veya FTP konumu burada uygulama yayımlanacak, örneğin d:\deploy girin. Ardından **sonraki** devam etmek için.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce Kullanarak Office Çözümü Dağıtma](http://msdn.microsoft.com/library/feb516b3-5e4d-449a-9fd2-347d08d90252)



