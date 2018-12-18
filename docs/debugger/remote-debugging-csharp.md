---
title: Uzaktan hata ayıklama bir C# veya VB projesi | Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 82873b29a173209739497087a4dfe5b293123e2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055666"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Uzaktan hata ayıklama Visual Studio'da C# veya Visual Basic projesi
Farklı bir bilgisayara dağıtılan bir Visual Studio uygulamasında hata ayıklamak için yükleme ve uzak Araçlar, uygulamanızın dağıtıldığı bilgisayarda çalıştırın, projenizi Visual Studio'dan uzak bilgisayara bağlanmak için yapılandırın ve ardından uygulamanızı çalıştırın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
Uzaktan hata ayıklama Evrensel Windows uygulamaları (UWP) hakkında daha fazla bilgi için bkz. [bir yüklenen uygulama paketinin hatalarını ayıklama](debug-installed-app-package.md).

## <a name="requirements"></a>Gereksinimler

Desteklenen Windows 7 ve daha yeni uzaktan hata ayıklayıcı (telefon değil) ve Windows Server 2008 Service Pack 2'ile başlayan Windows Server sürümleri. Gereksinimlerinin tam listesi için bkz. [gereksinimleri](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Bir proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmiyor. Ülkeler yüksek gecikme süresi veya çevirmeli, Internet gibi düşük bant genişliği bağlantı üzerinden veya Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya edilemeyecek kadar yavaş.
  
## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Bazı senaryolarda, uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırma en verimli olabilir. Daha fazla bilgi için [uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırma](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Uzaktan hata ayıklayıcı ayarlayın

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Gerektiğinde ek kullanıcılar için izinler eklemek için kimlik doğrulama modunu değiştirmek veya bağlantı noktası numarası için uzaktan hata ayıklayıcı değilse [uzaktan hata ayıklayıcı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a> Uzaktan hata ayıklama projesi
Hata ayıklayıcı uzak makinede Visual C# veya Visual Basic Masaüstü uygulamalar dağıtamazsınız, ancak yine de bunları aşağıdaki gösterildiği gibi uzaktan hata ayıklama. Aşağıdaki yordamda adlı bir bilgisayarda hata ayıklamak istediğiniz varsayılmaktadır **MJO DL**, aşağıdaki çizimde gösterildiği gibi.
  
1. Adlı bir WPF projesi oluşturma **MyWpf**.  
  
2. Bir kesme noktası herhangi bir kolayca ulaşıldığında kodda ayarlayın.  
  
    Örneğin, bir düğme işleyicisinde bir kesme noktası ayarlayabilirsiniz. Bunu yapmak için MainWindow.xaml açın ve araç kutusundan bir düğme denetimi ekleyin ve onun işleyicisi açmak için düğmeyi çift tıklatın.
  
3. Çözüm Gezgini'nde projeye sağ tıklayıp seçin **özellikleri**.  
  
4. Üzerinde **özellikleri** sayfasında **hata ayıklama** sekmesi.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Emin **çalışma dizini** metin kutusu boştur.  
  
6. Seçin **uzak makine**ve türü **MJO-DL:4022** metin kutusuna. (4022 uzaktan hata ayıklayıcı penceresinde gösterilen bağlantı noktası numarasıdır. Bağlantı noktası numarasını artırır 2. Visual Studio'nun her sürümü).
  
7. Emin olun **yerel kod hata ayıklamayı** seçilmez.  
  
8. Projeyi oluşturun.  
  
9. Uzak bilgisayarda aynı yol üzerinde bir klasör oluşturun **hata ayıklama** Visual Studio'nun bilgisayarınızda klasörünü:  **\<kaynak yolu > \MyWPF\MyWPF\bin\Debug**.  
  
10. Yalnızca Visual Studio bilgisayarınızdan için yeni oluşturulan klasör uzak bilgisayarda oluşturulan yürütülebilir dosya kopyalayın.
  
    > [!CAUTION]
    >  Değişiklik kod veya yeniden yapmayın (veya bu adımı tekrarlamalısınız). Yerel kaynak ve simgeler, uzak makineye kopyaladığınız yürütülebilir dosyanın tam olarak eşleşmelidir.

    Projeyi el ile kopyalayın, Xcopy, Robocopy, Powershell veya diğer seçenekleri kullanın.
  
11. Uzaktan hata ayıklayıcı, hedef makinede çalıştığından emin olun (yüklü değilse, arama **uzaktan hata ayıklayıcı** içinde **Başlat** menü). Uzaktan hata ayıklayıcı penceresini aşağıdaki gibi görünür.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Visual Studio'da hata ayıklamayı Başlat (**hata ayıklama > hata ayıklamayı Başlat**, veya **F5**).  
  
13. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.  
  
     Gerekli kimlik bilgilerinin, ağınızın güvenlik yapılandırmasına bağlı olarak farklılık gösterir. Örneğin, bir etki alanı bilgisayarında etki alanı adınızı ve parolanızı girebilirsiniz. Bir etki alanı olmayan makinede, makine adı ve geçerli kullanıcı hesabı adı gibi girebilirsiniz <strong>MJO-DL\name@something.com</strong>, doğru parola ile birlikte.

     WPF uygulamanın ana pencere uzak bilgisayarda açık olduğunu görmeniz gerekir.
  
14. Gerekirse, kesme noktasına isabet için gerekeni yapın. Kesme noktası etkin olduğunu görmeniz gerekir. Aksi takdirde, uygulama için semboller henüz. Yeniden deneyin ve bu işe yaramazsa, sembolleri yükleme hakkında bilgi edinin ve onları ilgili sorunları nasıl [sembol dosyalarını anlama ve Visual Studio'nun sembol ayarları](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Visual Studio makinede yürütme kesme noktasında durduruldu görmeniz gerekir.
  
    Uygulama tarafından kullanılması gereken herhangi bir kod dışı dosyalara varsa, bunları Visual Studio projenize eklemeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun (içinde **Çözüm Gezgini**, tıklayın **Ekle > Yeni klasör**). Dosyaları klasöre eklersiniz (içinde **Çözüm Gezgini**, tıklayın **Ekle > var olan öğe**, ardından dosyaları seçin). Üzerinde **özellikleri** sayfasında her dosya için **çıkış dizinine Kopyala** için **her zaman Kopyala**.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgeleri ile hata ayıklamayı kurma 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’da hata ayıklama](../debugger/index.md)  
 [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)   
 [Uzaktan hata ayıklama için Windows Güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)   
 [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)