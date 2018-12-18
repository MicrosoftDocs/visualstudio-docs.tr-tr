---
title: Önyükleyici paketleri oluşturma
ms.custom: ''
ms.date: 05/02/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a16044657b197229253f93fc6aea6130a4522f64
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512190"
---
# <a name="create-bootstrapper-packages"></a>Önyükleyici paketleri oluşturma
Kurulum programı gibi Windows Installer yeniden dağıtılabilir bileşenleri yüklemek ve algılamak için yapılandırılabilen genel bir yükleyicidir (*.msi*) dosyaları ve yürütülebilir programlar. Yükleyici bir önyükleyici de denir. Bu bileşenin yüklenmesini yönetmek için meta verileri belirleyen XML bildirimleri kümesi programlanır.  Her yeniden dağıtılabilir bileşeni, ya da önkoşul, görünür **önkoşulları** iletişim kutusu için ClickOnce önyükleyici paketi olur. Bir önyükleyici paketi, dizinler ve önkoşul nasıl yükleneceğini açıklayan bildirim dosyalarını içeren dosyaları grubudur. 
  
Önyükleyici önce Önkoşullar zaten yüklü olup olmadığını algılar. İlk Önkoşullar yüklü değilse, önyükleyici lisans sözleşmelerini gösterir. İkinci olarak, son kullanıcı lisans sözleşmelerini kabul ettikten sonra yükleme Önkoşullar için başlar. Aksi takdirde, tüm ön koşullar algılanırsa, önyükleyici yalnızca uygulama yükleyicisini başlatır.  
  
## <a name="create-custom-bootstrapper-packages"></a>Özel önyükleyici paketleri oluşturma  
Visual Studio XML Düzenleyicisi'ni kullanarak, önyükleyici bildirimler oluşturabilirsiniz. Bir önyükleyici paketi oluşturma örneği için bkz [izlenecek yol: bir gizlilik istemiyle özel bir önyükleyici oluşturma](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
Bir önyükleyici paketi oluşturmak için ürün bildirimi oluşturmanız gerekir ve her biri için yerelleştirilmiş bir paket bildirimi de bir bileşen sürümü.
  
* Ürün bildirimi *product.xml*, paket için dilden meta verileri içerir. Bu yeniden dağıtılabilir bileşenin tüm yerelleştirilmiş sürümleri için ortak meta veriler içerir.  Bu dosyayı oluşturmak için bkz: [nasıl yapılır: bir ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md).
  
* Paket bildirimi *package.xml*, dile özgü meta veriler; içeren genellikle yerelleştirilmiş hata iletileri içerir. Bir bileşen, yerelleştirilmiş her bileşenin sürümü için en az bir paket bildiriminin olması gerekir. Bu dosyayı oluşturmak için bkz: [nasıl yapılır: bir paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).
  
Bu dosyalar oluşturulduktan sonra ürün bildirim dosyasını özel önyükleyici için adlandırılan bir klasöre yerleştirin. Paket bildirim dosyası yerel ayar adlı bir klasöre gider. Örneğin, paket bildirim dosyasının İngilizce olarak yeniden dağıtılması için ise, dosyayı en adlı klasöre koyun. Japonca için ja ve Almanca için de gibi her yerel ayar için bu işlemi yineleyin. Son özel önyükleyici paketi aşağıdaki klasör yapısına sahip olabilir.  

    ```xml
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```
  
Ardından, yeniden dağıtılabilen dosyaları önyükleyici klasör konumuna kopyalayın. Daha fazla bilgi için [nasıl yapılır: yerelleştirilmiş önyükleyici paketi oluşturma](../deployment/how-to-create-a-localized-bootstrapper-package.md).
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
veya  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
Aynı zamanda önyükleyici klasör konumunu da belirleyebilirsiniz **yolu** aşağıdaki kayıt defteri değeri:  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
64-bit sistemlerde, aşağıdaki kayıt defteri anahtarını kullanın:  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
Yeniden dağıtılabilir her bileşen paketler dizini altında kendi alt klasöründe görünür. Gereken ürün bildirimi ve yeniden dağıtılabilir dosyaları, bu alt klasöre yerleştirin. Bileşen ve paket bildirim dosyalarının yerelleştirilmiş sürümleri, kültür adı göre adlandırılan alt klasörlere içinde yerleştirmeniz gerekir.  
  
Bu dosyalar önyükleyici klasörüne kopyalandıktan sonra önyükleyici paketi otomatik olarak Visual Studio'da görünür **önkoşulları** iletişim kutusu. Özel önyükleyici paketiniz görünmüyorsa kapatıp **önkoşulları** iletişim kutusu. Daha fazla bilgi için [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).  
  
Aşağıdaki tablo önyükleyici tarafından otomatik olarak doldurulan özellikleri gösterir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|ApplicationName|Uygulamanın adı.|  
|ProcessorArchitecture|İşlemci ve BITS başına word bir yürütülebilir dosya tarafından hedeflenen platformun. Değerler aşağıdakileri içerir:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95, Windows 98 veya Windows ME işletim sistemlerine ilişkin sürüm numarasıdır. Sürümün sözdizimi Major.Minor.ServicePack öğesidir.|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 veya Windows 7 işletim sistemlerine ilişkin sürüm numarasıdır. Sürümün sözdizimi Major.Minor.ServicePack öğesidir.|  
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Windows Installer derlemesinin (msi.dll) yükleme sırasında çalıştırılacak sürümü.|  
|[AdminUser](/windows/desktop/Msi/adminuser)|Bu özellik, kullanıcının yönetici ayrıcalıkları varsa ayarlanır. Değerler şunlardır: true veya false.|  
|InstallMode|Yükleme modu bileşenin nereden yüklenmesi gereken yere gösterir. Değerler aşağıdakileri içerir:<br /><br /> -HomeSite - Önkoşullar satıcının Web sitesinden yüklenir.<br />-SpecificSite - Önkoşullar seçtiğiniz konumdan yüklenir.<br />-SameSite - Önkoşullar uygulama ile aynı konumdan yüklenir.|  
  
## <a name="separate-redistributables-from-application-installations"></a>Uygulama yüklemelerini alanından ayrı yeniden dağıtılabilir  
Yeniden dağıtılabilir dosyaların Kurulum projelerinde dağıtılmasını engelleyebilirsiniz. Bunu yapmak için .NET Framework dizininiz içindeki RedistList klasöründe bir yeniden dağıtılabilir liste oluşturun:  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
Yeniden dağıtılabilir liste, aşağıdaki biçimi kullanarak adlandırmalısınız. bir XML dosyasıdır:  *\<şirket adı >.\< Bileşen adı >. RedistList.xml*. Bu nedenle, örneğin bileşen Acme tarafından yapılan DataWidgets olarak adlandırılmışsa, kullanın *Acme.DataWidgets.RedistList.xml*. Yeniden dağıtılabilir liste içeriklerinin bir örneği şuna benzeyebilir:  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md)   
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)   
 [Yüklemenizi başlatmak için Visual Studio 2005 bootstrapper kullanın](http://go.microsoft.com/fwlink/?LinkId=107537)
