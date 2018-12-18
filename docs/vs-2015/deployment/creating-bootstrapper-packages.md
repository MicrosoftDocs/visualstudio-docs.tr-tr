---
title: Önyükleyici paketleri oluşturma | Microsoft Docs
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
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: dcc331defab98303a805f75f75afb3e309c7d2dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910933"
---
# <a name="creating-bootstrapper-packages"></a>Önyükleyici Paketleri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kurulum programı Windows Installer (.msi) dosyaları ve yürütülebilir programlar gibi yeniden dağıtılabilir bileşenleri yüklemek ve algılamak için yapılandırılabilen genel bir yükleyicidir. Yükleyici bir önyükleyici de denir. Bu bileşenin yüklenmesini yönetmek için meta verileri belirleyen XML bildirimleri kümesi programlanır.  
  
 Önyükleyici önce Önkoşullar zaten yüklü olup olmadığını algılar. İlk Önkoşullar yüklü değilse, önyükleyici lisans sözleşmelerini gösterir. İkinci olarak, son kullanıcı lisans sözleşmelerini kabul ettikten sonra yükleme Önkoşullar için başlar. Aksi takdirde, tüm ön koşullar algılanırsa, önyükleyici yalnızca uygulama yükleyicisini başlatır.  
  
## <a name="creating-custom-packages"></a>Özel paketler oluşturma  
 Visual Studio XML Düzenleyicisi'ni kullanarak bildirimler oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md) ve [nasıl yapılır: bir ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md). Bir önyükleyici paketi oluşturma örneği için bkz [izlenecek yol: bir gizlilik istemi göstermek için özel bir önyükleyici oluşturma](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Bir önyükleyici paketi oluşturma için yeniden dağıtılabilir bir EXE or MSI öğeyi Önyükleyici Bildirim Oluşturucusu biçiminde sağlamanız gerekir. Sonra Önyükleyici Bildirim Oluşturucusu aşağıdaki dosyaları oluşturur:  
  
- Ürün bildirimi, paket için dilden meta verileri içeren product.xml. Bu yeniden dağıtılabilir bileşenin tüm yerelleştirilmiş sürümleri için ortak meta veriler içerir.  
  
- Paket bildirimi, dile özgü meta veriler içeren package.xml; Genellikle, yerelleştirilmiş hata iletileri içerir. Bir bileşen, yerelleştirilmiş her bileşenin sürümü için en az bir paket bildiriminin olması gerekir.  
  
  Bu dosyalar oluşturulduktan sonra ürün bildirim dosyasını özel önyükleyici için adlandırılan bir klasöre yerleştirin. Paket bildirim dosyası yerel ayar adlı bir klasöre gider. Örneğin, paket bildirim dosyasının İngilizce olarak yeniden dağıtılması için ise, dosyayı en adlı klasöre koyun. Japonca için ja ve Almanca için de gibi her yerel ayar için bu işlemi yineleyin. Son özel önyükleyici paketi aşağıdaki klasör yapısına sahip olabilir.  
  
  `CustomBootstrapperPackage`  
  
  `product.xml`  
  
  `CustomBootstrapper.msi`  
  
  `de`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `en`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `ja`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  Son olarak, yeniden dağıtılabilen dosyaları önyükleyici klasör konumuna kopyalayın. Daha fazla bilgi için [nasıl yapılır: yerelleştirilmiş önyükleyici paket oluşturma](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 veya  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Aynı zamanda önyükleyici klasör konumunu da belirleyebilirsiniz **yolu** aşağıdaki kayıt defteri değeri:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 64 bit sistemlerde, aşağıdaki kayıt defteri anahtarını kullanın:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Yeniden dağıtılabilir her bileşen paketler dizini altında kendi alt klasöründe görünür. Ürün bildirimi ve yeniden dağıtılabilir dosyaları, bu alt klasöre konur. Bileşen ve paket bildirim dosyalarının yerelleştirilmiş sürümleri, kültür adı göre adlandırılan alt klasörlere yerleştirilir.  
  
 Bu dosyalar önyükleyici klasörüne kopyalandıktan sonra önyükleyici paketi otomatik olarak Visual Studio önkoşulları iletişim kutusunda görüntülenir. Özel önyükleyici paketiniz görünmüyorsa kapatın ve ardından Önkoşullar iletişim kutusunu açın. Daha fazla bilgi için [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).  
  
 Aşağıdaki tablo önyükleyici tarafından otomatik olarak doldurulan özellikleri gösterir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|ApplicationName|Uygulamanın adı.|  
|ProcessorArchitecture|İşlemci ve BITS başına word bir yürütülebilir dosya tarafından hedeflenen platformun. Değerler aşağıdakileri içerir:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Microsoft Windows 95, Windows 98 veya Windows ME işletim sistemlerine ilişkin sürüm numarasıdır. Sürümün sözdizimi Major.Minor.ServicePack öğesidir.|  
|[VersionNT](https://msdn.microsoft.com/library/aa372495\(v=vs.140\).xaspx)|Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 veya Windows 7 işletim sistemlerine ilişkin sürüm numarasıdır. Sürümün sözdizimi Major.Minor.ServicePack öğesidir.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|Windows Installer derlemesinin (msi.dll) sürümü, yükleme sırasında çalıştırın.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Bu özellik, kullanıcının yönetici ayrıcalıkları varsa ayarlanır. Değerler şunlardır: true veya false.|  
|InstallMode|Yükleme modu bileşenin nereden yüklenmesi gereken yere gösterir. Değerler aşağıdakileri içerir:<br /><br /> -HomeSite - Önkoşullar satıcının Web sitesinden yüklenir.<br />-SpecificSite - Önkoşullar seçtiğiniz konumdan yüklenir.<br />-SameSite - Önkoşullar uygulama ile aynı konumdan yüklenir.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Yeniden dağıtılabilir dosyaları, uygulama yüklemelerinden ayırma  
 Yeniden dağıtılabilir dosyaların Kurulum projelerinde dağıtılmasını engelleyebilirsiniz. Bunu yapmak için .NET Framework dizininiz içindeki RedistList klasöründe bir yeniden dağıtılabilir liste oluşturun:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Yeniden dağıtılabilir liste, aşağıdaki biçimi kullanarak adlandırmalısınız. bir XML dosyasıdır: *şirket adı*. *Bileşen adı*. RedistList.xml. Bu nedenle, bileşen Acme tarafından yapılan Datawidgets olarak adlandırılmışsa, örneğin, Acme.DataWidgets.RedistList.xml kullanın. Yeniden dağıtılabilir liste içeriklerinin bir örneği şuna benzeyebilir:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md)   
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)   
 [Yüklemenize başlamak için Visual Studio 2005 Bootstrapper kullanın](http://go.microsoft.com/fwlink/?LinkId=107537)



