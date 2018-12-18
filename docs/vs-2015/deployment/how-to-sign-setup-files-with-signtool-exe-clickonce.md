---
title: 'Nasıl yapılır: Kurulum dosyalarını SignTool.exe (ClickOnce) ile | Microsoft Docs'
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
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f6975fb9c3c3e1abeeaebe23b4a85f41833e421e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179315"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Nasıl yapılır: Kurulum Dosyalarını SignTool.exe ile İmzalama (ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SignTool.exe bir Kurulum programı (setup.exe) oturum açmak için kullanabilirsiniz. Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklü olmadığını garanti eder.  
  
 Varsayılan olarak, ClickOnce bildirimlerini ve imzalı bir Kurulum programı oturum açtı. Ancak, daha sonra Kurulum programının parametreleri değiştirmek istiyorsanız, Kurulum programı daha sonra oturum açmalısınız. Kurulum programı açtıktan sonra parametreleri değiştirin, imza bozulur.  
  
 Aşağıdaki yordam, imzalanmamış bildirimler ve imzalanmamış bir Kurulum programı oluşturur. Ardından, ClickOnce imzalama Visual Studio'da imzalı bildirimler oluşturmak için etkinleştirilir. Müşteri yürütülebilir dosya, kendi sertifika ile oturum açabilirsiniz, böylece Kurulum programı sol imzalanmamış.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>İmzalanmamış bir Kurulum programı oluşturun ve daha sonra oturum için  
  
1.  Geliştirme bilgisayarında oturum bildirimleri istediğiniz sertifikayı yükleme ile.  
  
2.  Projede seçin **Çözüm Gezgini**.  
  
3.  Üzerinde **proje** menüsünde tıklatın *ProjectName* **özellikleri**.  
  
4.  İçinde **imzalama** sayfasında, NET **ClickOnce bildirimlerini imzala**.  
  
5.  İçinde **Yayımla** sayfasında **önkoşulları**.  
  
6.  Tüm Önkoşullar seçilir ve ardından doğrulamak **Tamam**.  
  
7.  İçinde **Yayımla** sayfasında yayınlama ayarları doğrulayın ve ardından **Şimdi Yayımla**.  
  
     İmzasız uygulama bildirimi, işaretsiz bir dağıtım bildirimi, sürümüne özel dosyalar ve imzalanmamış bir Kurulum programı, çözümü yayımlama klasörü konumu için yayımlar.  
  
8.  İçinde **Yayımla** sayfasında **önkoşulları**.  
  
9. İçinde **önkoşulları** iletişim kutusu, NET **Önkoşul bileşenlerini yüklemek için Kurulum programını Oluştur**.  
  
10. İçinde **Yayımla** sayfasında yayınlama ayarları doğrulayın ve ardından **Şimdi Yayımla**.  
  
     Çözüm yayımlama klasörü konumu için imzalı bir uygulama bildirimi, imzalı dağıtım bildirimini ve sürümüne özel dosyalar yayımlar. İmzalanmamış bir Kurulum programı yayımlama işlemi tarafından üzerine yazılır.  
  
11. Müşteri sitede, bir komut istemi açın.  
  
12. .Exe dosyasını içeren dizine geçin.  
  
13. Aşağıdaki komutla .exe dosyasını imzalayın:  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Örneğin, Kurulum programını imzalamak için aşağıdaki komutlardan birini kullanın:  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Uygulama ve Dağıtım Bildirimlerini Yeniden İmzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)



