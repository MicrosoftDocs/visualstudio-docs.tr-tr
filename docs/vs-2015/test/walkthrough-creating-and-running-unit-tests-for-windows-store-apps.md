---
title: 'İzlenecek yol: Oluşturma ve Windows Store uygulamaları için birim testleri çalıştıran | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: gewarren
manager: douge
ms.openlocfilehash: 30a8b7a465c85e60b00f2208bd6e51cc55c4bbe7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852537"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>İzlenecek yol: Windows Mağazası Uygulamaları için Birim Testleri Oluşturma ve Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio birim testi yönetilen için destek içerir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar ve Visual C#, Visual Basic ve Visual C++ için birim sınaması kitaplığı şablonları içerir.  
  
> [!TIP]
>  Geliştirme hakkında daha fazla bilgi için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar, [Windows Store uygulamaları kullanmaya başlama](http://go.microsoft.com/fwlink/?LinkID=241410).  
  
 Visual Studio aşağıdaki birim sınama işlevleri sağlar:  
  
- [Birim testi projeleri oluşturma](#CreateAndRunUnitTestWin8Tailored_Create)  
  
- [Birim Test projesi için bildirimi düzenleyin](#CreateAndRunUnitTestWin8Tailored_Manifest)  
  
- [Birim testini kodlama](#CreateAndRunUnitTestWin8Tailored_Code)  
  
- [Birim testleri çalıştırma](#CreateAndRunUnitTestWin8Tailored_Run)  
  
  Aşağıdaki yordamlar oluşturma, çalıştırma ve yönetilen Windows 8 için birim testlerinin hatalarını ayıklama adımlarını açıklamaktadır [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Birim testi projeleri oluşturma  
  
#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Bir Windows Store uygulaması için birim test projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünde seçin **yeni proje**.  
  
     Yeni Proje iletişim kutusu görüntüler.  
  
2.  Şablonlar'ın altında birim sınamasını oluşturmak ve ardından ilişkili programlama dili [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] birim testi kitaplığı. Örneğin, **Visual C#** , ardından **Windows Store**ve ardından **birim testi kitaplığı (Windows Store apps)**.  
  
    > [!NOTE]
    >  Visual Studio, Visual C#, Visual Basic ve Visual C++ için birim sınaması kitaplığı şablonları içerir.  
  
3.  (İsteğe bağlı) İçinde **adı** metin için kullanmak istediğiniz adı girin [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]birim testi projesi.  
  
4.  (İsteğe bağlı) Girerek projeyi oluşturmak istediğiniz yolu değiştirmek **konumu** metin veya belirleyerek **Gözat** düğmesi.  
  
5.  (İsteğe bağlı) İçinde **çözüm** ad metin kutusunda, çözümünüz için kullanmak istediğiniz ismi girin.  
  
6.  Bırakın **çözüm için dizin oluştur** seçeneği seçili ve seçin **Tamam** düğmesi.  
  
     ![Birim testi kitaplığı uyarlanmış](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")  
  
     Çözüm Gezgini doldurulur yeni [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]birim test projesi ve Kod Düzenleyicisi, UnitTest1 başlıklı varsayılan birim sınamasını görüntüler.  
  
     ![Yeni özel olarak uyarlanmış bir birim test projesi](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Birim Test projesi için bildirimi düzenleyin  
 Uygulamayı çalıştırmak için gereken kabiliyetleri sağlamak birim test projesi için bildirimi düzenlemek gerekli olabilir.  
  
#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Birim test projesinin Windows Store uygulama bildirim dosyasını düzenlemek için  
  
1.  Çözüm Gezgini'nde, yeni [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] birim test projesinde Package.appxmanifest dosyasını sağ tıklatın ve seçin **açık**.  
  
     Bildirim Tasarımcısı, düzenleme için görüntüler.  
  
2.  Bildirim Tasarımcısı'nda **özellikleri** sekmesi.  
  
3.  Listenin altında **özellikleri**, birim sınamanız ve kod gereken yetenekleri seçin sahip sınamanız. Örneğin, **Internet** birim testi ve test ettiği kodun onay kutusu İnternet'e erişme özelliği olması gerekir.  
  
    > [!NOTE]
    >  Seçtiğiniz yetenekler yalnızca için gerekli olan yetenekleri içermelidir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] düzgün çalışması için birim testi. Özellikleri hiçbir zaman olmayan yetenekleri içermesi gerekmez parçası [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamasının genellikle için belirtilen yeteneklerin bir alt kümesi olmalıdır ve test [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]test altındaki uygulama.  
  
     Bildirim Tasarımcısı hakkında daha fazla bilgi için bkz: [bildirim Tasarımcısını kullanarak bir Windows 8.1 uygulama paketini Yapılandır](http://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).  
  
     ![Birim Test bildirimi](../test/media/unit-test-win8.png "Unit_Test_Win8_")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Birim testini kodlama  
  
#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Bir Windows Store uygulaması için birim testi kodu  
  
1.  Kod Düzenleyicisi'nde, birim sınamasını düzenleyin ve ekleyin onaylar ve sınama için gereken mantığı.  
  
     Daha fazla bilgi için bkz [onay sınıfları](http://go.microsoft.com/fwlink/?LinkID=224991) MSDN Kitaplığı'nda.  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Birim testleri çalıştırma  
  
#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Çözümü derleyin ve Test Gezgini'ni kullanarak birim testini çalıştırmak için  
  
1.  Üzerinde **Test** menüsünde seçin **Windows**ve ardından **Test Gezgini**.  
  
     Explorer görüntüler listelenmesini, testiniz listelenmeden.  
  
2.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.  
  
     Birim testiniz artık listelenir.  
  
    > [!NOTE]
    >  Test Gezgini'nde birim testleri listesini güncelleme çözümünü oluşturmanız gerekir.  
  
    > [!WARNING]
    >  Visual Studio bilinen sorun: test projesini oluşturmadan önce Test Gezgini'ni açmanız gerekir.  
  
3.  Test Gezgini'nde oluşturduğunuz birim sınamayı seçin.  
  
    > [!TIP]
    >  Test Gezgini kaynak koda bir bağlantı yanındaki sağlar **kaynak:**.  
  
4.  Seçin **çalıştırması**.  
  
     ![Birim Test Gezgini &#45; birim testi çalıştırma](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")  
  
    > [!TIP]
    >  Explorer'da listelenen bir veya daha fazla birim testleri seçebilir ve ardından sağ tıklatın ve seçin **seçili Testleri Çalıştır**.  
    >   
    >  Ayrıca, seçebileceğiniz **seçilen Testlerde Hata Ayıkla**, **açık Test**ve **özellikleri** seçeneği.  
    >   
    >  ![Birim Test Gezgini &#45; UNI test bağlam menüsü](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")  
  
     Birim testi çalışır. Tamamlandıktan sonra Test Gezgini test durumunu, geçen süreyi görüntüler ve kaynağa bir bağlantı sağlar.  
  
     ![Birim Test Gezgini &#45; test tamamlandı](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
### <a name="videos"></a>Videolar  
 [Kanal 9: XAML kullanılarak oluşturulan, Windows Store uygulamalarını test etme birim](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Forumlar  
 [Visual Studio birim testi](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="msdn-library"></a>MSDN Kitaplığı  
 [MSDN Kitaplığı – oluşturma ve (Visual Studio 2010) var olan kod için birim testleri çalıştırma](http://go.microsoft.com/fwlink/?LinkID=223683)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio ile Store uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md)   
 [Yapı ve test Team Foundation Yapısı kullanarak Windows Store uygulaması](http://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)



