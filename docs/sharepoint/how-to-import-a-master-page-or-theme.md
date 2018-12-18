---
title: 'Nasıl yapılır: bir ana sayfa veya temayı içeri aktarma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 116ab878d8591fb15bfbb319b2c1d79952fbd0e7
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120608"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Nasıl yapılır: bir ana sayfa veya temayı içeri aktarma
  Sayfalar, SharePoint sitesinde tutarlı bir görünüm oluşturma ve ana sayfalar ve Temalar kullanma verebilirsiniz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Bu öğeler için şablonlar sağlamaz, ancak bunları SharePoint Tasarımcısı'nda oluşturabilir ve bunları almak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Daha fazla bilgi için bkz: [yapı taşı: sayfaları ve kullanıcı arabirimi](http://go.microsoft.com/fwlink/?LinkID=182095) Microsoft Web sitesinde.  
  
### <a name="to-import-a-master-page-or-theme"></a>Bir ana sayfa veya temayı içeri aktarmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]oluşturun veya bir SharePoint proje açın.  
  
     Bir SharePoint Proje oluşturma hakkında daha fazla bilgi için bkz: [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Menü çubuğunda seçin **proje** > **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, genişletin **SharePoint** düğümünü ve ardından **2010** düğümü.  
  
4.  SharePoint şablonları listesinden seçip **Modülü** şablonu ve modül için bir ad belirtin.  
  
     Bir modül, SharePoint'te belirttiğiniz bir konuma dağıtımı için (örneğin, ana sayfa veya temayı dosyaları) dosyalarını içerir.  
  
5.  Modülde adlı varsayılan dosya silme *örnek.txt*.  
  
6.  Modül düğümünü seçin.  
  
7.  Menü çubuğunda seçin **proje** > **varolan öğeyi Ekle**ve ardından ana sayfa veya temayı dosya seçin.  
  
     Ana sayfa dosyalar .master uzantısına sahiptir ve tema dosyalar .thmx uzantısına sahiptir.  
  
8.  Bir ana sayfa eklediyseniz, değiştirme, **dağıtım Çakışma çözümlemesi** ayarını **otomatik** modülün özellikleri.  
  
    > [!NOTE]  
    >  Ana sayfa adını varsayılan ana sayfa veya özel bir ana sayfa olarak işaretlenmiş var olan bir ana sayfa adı ile aynı olduğunda hatalar oluşabilir. Bu sorunun nasıl çözüleceği hakkında daha fazla bilgi için bkz: [izlenecek yol: bir özel ana sayfa ve site sayfasını bir görüntüyle alma](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Modül açmak *Elements.xml*.  
  
     Güncelleştirmeniz gerekir *Elements.xml* ana sayfa veya eklediğiniz tema başvurmak için dosya.  
  
10. Bir ana sayfa için varolan modülü biçimlendirme aşağıdaki biçimlendirme ile değiştirin.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Bir tema için varolan modülü biçimlendirme aşağıdaki biçimlendirme ile değiştirin.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Yer tutucu değerlerini modülü ve ana sayfa veya temayı gerçek adlarını ile değiştirdiğinizden emin olun.  
  
     Öznitelik `Type="GhostableInLibrary"` öğe içerik veritabanına eklenir gösterir ve `Url` özniteliği modülün SharePoint içerik veritabanı dosyasının depolanacağı konumu belirtir.  
  
11. İçinde bir ana sayfa dağıtım kapsamını değiştirmek için **Çözüm Gezgini**, özellik Tasarımcısı'nda özelliği dosyasını açın ve ardından yeni bir dağıtım kapsamdan seçin **kapsam** listesi.  
  
     Değerini **Web** şu anda projede belirtilen Web sitesi ana sayfa uygulandığı anlamına gelir. Değerini **Site** ana sayfa tüm siteleri ve kök web içerir geçerli site koleksiyonuna uygulanır anlamına gelir. Diğer değerler uygulanmaz.  
  
    > [!NOTE]  
    >  Yalnızca site koleksiyonu düzeyinde Temalar geçerli olduğundan, bir tema kapsamı için herhangi bir şey dışında ayarlamanızı yok öneririz **Site**. Bir tema bir alt sitede kullandıysanız hatalar oluşabilir.  
  
12. Menü çubuğunda seçin **yapı** > **çözümü Dağıt**.  
  
13. Dosyaların doğru bir şekilde dağıtılıp dağıtılmadığını doğrulamak için SharePoint sitesini açın, seçin **Site eylemleri** menüsünde seçin **Site Ayarları** komutunu ve ardından ya da **ana sayfalar**  bağlantı veya **Temalar** bağlantı.  
  
     Ana sayfalar veya Temalar listesi görüntülenir ve ana sayfa veya içe aktardığınız tema içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Ana sayfalar](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint için sayfa oluşturma](../sharepoint/creating-pages-for-sharepoint.md)   
 [Çözüme dosyaları dahil etmek için modülleri kullanın](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
