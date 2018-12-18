---
title: 'Nasıl yapılır: Kurulum dosyalarını SignTool.exe (ClickOnce) ile | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b66d9440ebcf62c59049b45769a2244fc773480e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081507"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Nasıl yapılır: Kurulum dosyalarını SignTool.exe (ClickOnce) ile
Kullanabileceğiniz *SignTool.exe* Kurulum programını imzalamak için (*setup.exe*). Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklü olmadığını garanti eder.  
  
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
  
12. Değişiklik içeren dizine *.exe* dosya.  
  
13. Oturum *.exe* dosyasını aşağıdaki komutla:  
  
    ```cmd  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Örneğin, Kurulum programını imzalamak için aşağıdaki komutlardan birini kullanın:  
  
    ```cmd  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: yeniden, uygulama ve dağıtım bildirimlerini imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
