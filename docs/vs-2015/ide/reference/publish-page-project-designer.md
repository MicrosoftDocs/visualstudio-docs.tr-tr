---
title: Yayımlama Sayfası, Proje Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1dcd6660ff431bee76fb7f595ed243104136684d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277972"
---
# <a name="publish-page-project-designer"></a>Yayın Sayfası, Proje Tasarımcısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Yayımla** sayfasının **Proje Tasarımcısı** ClickOnce dağıtım özelliklerini yapılandırmak için kullanılır.  
  
 Erişim için **Yayımla** sayfasında, içinde bir proje düğümü seçin **Çözüm Gezgini**ve ardından **proje** menüsünde tıklayın **özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklayın **Yayımla** sekmesi.  
  
> [!NOTE]
>  Burada açıklanan ClickOnce özelliklerden bazıları da ayarlanabilir **PublishWizard**erişilebilir **derleme** menüsü veya tıklayarak **PublishWizard** bu düğmesi Sayfa.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Yayımlama klasörü konumu**  
 Burada uygulama yayınlandıktan konumu belirtir. Bir sürücü yolu (`C:\deploy\myapplication`), bir dosya paylaşımı (`\\server\myapplication`), bir FTP sunucusuna (`ftp://ftp.microsoft.com/myapplication`), veya bir Web sitesi (`http://www.microsoft.com/myapplication`). Metin mevcut olması gerektiğini unutmayın **yayımlama konumu** Gözat sırayla kutusuna (**...** ) çalışmaya düğmesi.  
  
 Varsayılan olarak, yayımlama konumdur `http://localhost/<projectname>/` , IIS yüklü değilse veya `publish\` IIS yüklü değilse dizin. Bilgisayarınızı Windows Vista çalıştırıyorsa, her zaman varsayılandır `publish\` IIS yüklü olup olmadığından bağımsız olarak dizin.  
  
 **Yükleme klasörü URL'si**  
 İsteğe bağlı. Bir Web sitesi, kullanıcıların uygulamayı yüklemek için Git belirtir. Bu yalnızca, bu farklıdır gereklidir **yayımlama konumu**, örneğin, ne zaman uygulama yayımlandığında bir hazırlık sunucusu için.  
  
 **Yükleme modu ve ayarları**  
 Uygulamayı doğrudan çalıştırılıp çalıştırılmadığını belirleyen **yayımlama konumu** (zaman **uygulama yalnızca çevrimiçi kullanılabilir** seçilir) veya yüklü ve eklenen **Başlat**  menü ve **Program Ekle veya Kaldır** öğesi **Denetim Masası** (zaman **uygulamayı çevrimdışı olarak da kullanılabilir** seçili).  
  
 WPF Web tarayıcı uygulamaları için **uygulamayı çevrimdışı olarak da kullanılabilir** seçeneği devre dışıdır, çünkü bu tür uygulamalar yalnızca çevrimiçi kullanılabilir.  
  
 **Uygulama dosyaları**  
 Açılır [uygulama dosya iletişim kutusu](http://msdn.microsoft.com/en-us/b06dff3a-b87a-4caf-996b-7a4acf8137a8), tek tek dosyaların nasıl ve nereye yüklendiğini belirtmek için kullanılır.  
  
 **Önkoşullar**  
 Açılır [Önkoşullar iletişim kutusu](../../ide/reference/prerequisites-dialog-box.md), uygulama ile birlikte yüklenmesi için .NET Framework gibi önkoşul bileşenleri belirtmek için kullanılır.  
  
 **Güncelleştirmeler**  
 Açılır [uygulama güncelleştirmeleri iletişim kutusu](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), uygulama için güncelleştirme davranışını belirtmek için kullanılır. Kullanılabilir olduğunda **uygulama yalnızca çevrimiçi kullanılabilir** seçilir.  
  
 **Seçenekler**  
 Açılır [Yayımlama Seçenekleri iletişim kutusu](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), Gelişmiş yayımlama seçeneklerini, ek belirtmek için kullanılır.  
  
 **Yayım sürümü**  
 Uygulama için yayımlama sürüm numarasını ayarlar; sürüm numarası değiştirildiğinde, uygulama bir güncelleştirme olarak yayımlanır. Yayınlama sürümünü her parçası (**ana**, **küçük**, **derleme**, **düzeltme**) 65355 maksimum değeri olabilir (<xref:System.UInt16.MaxValue>), tarafından izin verilen maksimum <xref:System.Version>.  
  
 ClickOnce kullanarak bir uygulamanın birden fazla sürüm yüklediğinizde, yükleme uygulamanın önceki sürümlerini belirttiğiniz yayımlama konum arşivinde adlı bir klasöre taşır. Yükleme dizini temizler önceki sürümünden önceki sürümleri bu şekilde korur arşivleme.  
  
 **Her yayımlamada otomatik artış**  
 İsteğe bağlı. Bu seçenek seçildiğinde (varsayılan), **düzeltme** Yayımla sürüm numarasının bölümü bir artırılır uygulamayı yayınladınız her zaman. Bu, bir güncelleştirme olarak yayımlanacak uygulama neden olur.  
  
 **Yayımlama Sihirbazı**  
 Açılır [Yayımlama Sihirbazı](http://msdn.microsoft.com/en-us/fc6abebd-13d6-48e4-a567-fbc52dad0872). Yayımlama Sihirbazı Tamamlanıyor çalışan aynı etkiye sahip **Yayımla** komutunu **derleme** menüsü.  
  
 **Şimdi Yayımla**  
 Geçerli ayarları kullanarak uygulamanın yayınlar. Eşdeğer **son** düğmesine **PublishWizard**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Nasıl yapılır: Visual Studio'nun dosyaları nereye kopyalayacağını belirtme](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Nasıl yapılır: son kullanıcıların yükleme yapacakları konumu belirtme](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [Nasıl yapılır: teknik destek için bir bağlantı belirtme](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [Nasıl yapılır: ClickOnce çevrimdışı belirtin veya çevrimiçi yükleme modunu](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [Nasıl yapılır: CD yüklemeleri için AutoStart'ı etkinleştirme](../../deployment/how-to-enable-autostart-for-cd-installations.md)   
 [Nasıl yapılır: ayarlama ClickOnce yayım sürümü](../../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Nasıl yapılır: otomatik olarak artırma ClickOnce yayım sürümü](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Nasıl yapılır: ClickOnce tarafından hangi dosyaların yayımlandığını belirtme](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)   
 [Nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için güncelleştirmeleri yönetme](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)   
 [Nasıl yapılır: değişiklik ClickOnce uygulaması için yayımlama dilini](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için Başlat menüsü adı belirtme](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [ClickOnce Güvenliği ve Dağıtımı](../../deployment/clickonce-security-and-deployment.md)



