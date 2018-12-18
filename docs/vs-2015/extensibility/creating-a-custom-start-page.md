---
title: Başlangıç sayfasına özel oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87f653a6ac745253ae86eb6bf8dfab92169ac4db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806067"
---
# <a name="creating-a-custom-start-page"></a>Özel Başlangıç Sayfası Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel bir başlangıç sayfası başlangıç sayfası proje şablonunu kullanarak açıklandığı oluşturamıyorsanız [başlangıç sayfaları](../misc/creating-your-own-start-page.md), el ile bu belgedeki adımları izleyerek bir tane oluşturabilirsiniz.  
  
## <a name="creating-a-blank-start-page"></a>Boş bir başlangıç sayfası oluşturma  
 İlk olarak, boş bir başlangıç sayfası, Visual Studio tanıyacağınız bir etiket yapısı olan bir .xaml dosyası oluşturarak olun. Ardından, biçimlendirme ve Görünüm ve işlevselliği istediğiniz üretmek için gerideki kod ekleyin.  
  
#### <a name="to-create-a-blank-start-page"></a>Boş bir başlangıç sayfası oluşturmak için  
  
1.  Yeni bir proje türü oluşturma **WPF uygulaması** (**Visual C# / Windows Masaüstü**.  
  
2.  Bir başvuru ekleyin `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  XAML dosyasını XML düzenleyicisinde açın ve üst düzey değiştirme \<penceresi > öğesine bir \<UserControl > öğesi olmadan herhangi bir ad alanı bildirimi kaldırılıyor.  
  
4.  Kaldırma `x:Class` en üst düzey öğe bildirimden. Bu XAML İçerik başlangıç sayfasını barındıran Visual Studio araç penceresi ile uyumlu hale getirir.  
  
5.  Aşağıdaki ad alanı bildirimi için üst düzey ekleme \<UserControl > öğesi.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Bu ad alanlarında, Visual Studio komutları, denetimleri ve UI ayarlarını erişim sağlar. Daha fazla bilgi için [bir başlangıç sayfası için Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Aşağıdaki örnek, boş bir başlangıç sayfası için .xaml dosyasında biçimlendirmeyi gösterir. Herhangi bir özel içerik içinde iç gideceğine <xref:System.Windows.Controls.Grid> öğesi.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Denetim eklemek için boş \<UserControl > özel başlangıç sayfası doldurmak için öğesi. Visual Studio'da belirli işlevselliği ekleme hakkında daha fazla bilgi için bkz: [bir başlangıç sayfası için Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Test ve özel uygulama başlangıç sayfası  
 Özel başlangıç sayfası, Visual Studio kilitlenmez doğrulayana kadar çalıştırmak için Visual Studio'nun birincil örneğine ayarlı değil. Bunun yerine, deneysel örneğinde test edin.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>El ile oluşturulan özel bir başlangıç sayfası test etmek için  
  
1.  XAML dosyanızın ve destekleyici metin dosyaları veya biçimlendirme dosyaları, çok kopya **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  klasör.  
  
2.  Başlangıç sayfanızı herhangi bir denetim veya Visual Studio yüklü olmayan bütünleştirilmiş kodlar içindeki türleri başvuruyorsa, derlemeleri kopyalamak ve ardından bunları yapıştırın _Visual Studio yükleme klasörü_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Bir Visual Studio komut isteminde **devenv /rootsuffix Exp** Visual Studio'nun deneysel örneği açın.  
  
4.  Deneysel örneğinde Git **Araçlar / Seçenekler / ortam / başlangıç** sayfasında ve XAML dosyanızı seçin **başlangıç sayfasını Özelleştir** açılır.  
  
5.  Üzerinde **görünümü** menüsünü tıklatın **başlangıç sayfası**.  
  
     Özel başlangıç sayfanızı görüntülenmesi gerekir. Dosyaları değiştirmek istiyorsanız, size gerekir deneysel örneği kapatın, değişiklik, kopyalayın ve değiştirilen dosyaları yapıştırın ve ardından değişiklikleri görüntülemek için deneysel örneğinde yeniden açın.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Uygulamaya özel başlangıç sayfasına Visual Studio birincil örneğinde  
  
-   Başlangıç sayfası test ve kararlı buldu sonra kullanın **başlangıç sayfasını Özelleştir** seçeneğini **seçenekleri** birincil örneğinde Visual Studio Başlangıç sayfası olarak seçmek için iletişim kutusu  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Başlangıç sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Başlangıç sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)   
 [Bir başlangıç sayfasına Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [İzlenecek yol: Kullanıcı ayarlarını başlangıç sayfasına kaydetme](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Özel Başlangıç Sayfaları Dağıtma](../extensibility/deploying-custom-start-pages.md)

