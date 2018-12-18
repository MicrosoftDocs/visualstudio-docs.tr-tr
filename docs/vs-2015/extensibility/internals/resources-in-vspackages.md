---
title: Vspackage'lardaki kaynaklar | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f6330055eb3e7b410cc71dc7bab9bc55769c4fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725324"
---
# <a name="resources-in-vspackages"></a>VSPackage’lardaki Kaynaklar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yerel Uydu DLL'leri kullanıcı Arabirimi, yönetilen Uydu DLL'leri, veya bir yönetilen VSPackage yerelleştirilmiş kaynaklar ekleyebilirsiniz.  
  
 Bazı kaynaklar Vspackage'larda eklenemiyor. Aşağıdaki yönetilen türler eklenebilir:  
  
- Dizeler  
  
- (Bu da dizelerdir) paket yük anahtarları  
  
- Araç penceresi simgeleri  
  
- Derlenmiş komutu tablo çıktı (CTO) dosyaları  
  
- CTO bit eşlemler  
  
- Komut satırı Yardımı  
  
- Hakkında iletişim kutusu verileri  
  
  Yönetilen paket kaynakları kaynak kimliğine göre seçilir. Bir özel durum CTMENU adlandırılmalıdır CTO dosyasıdır. CTO dosyanın kaynak tabloda yer görünmelidir bir `byte[]`. Diğer tüm kaynak öğelerini türe göre tanımlanır.  
  
  Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> belirtmek için özniteliği [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yönetilen kaynaklar kullanılabilir.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  Ayarı <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> bu şekilde bildiren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yönetilmeyen Uydu DLL'leri, kaynaklar için örneğin, kullanarak ararken sayılmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Varsa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aynı kaynak Kimliğine sahip iki veya daha fazla kaynak karşılaştığında bulduğu ilk kaynak kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir araç penceresi simge yönetilen bir gösterimidir.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 Aşağıdaki örnek CTMENU adlandırılmalıdır CTO bayt dizisi ekleme gösterir.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Uygulama Notları  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mümkün olduğunda VSPackages yüklenmesini gecikmeler. VSPackage'ı CTO dosya ekleme bir sonuç [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birleştirilmiş komut tablosu oluşturduğunda, Kurulum sırasında tüm bu tür bellek Vspackage'larda yüklemeniz gerekir. Kaynaklar meta verileri inceleyerek VSPackage içinde kod çalıştırmadan VSPackage ayıklanabilir. VSPackage'ı en düşük performans kaybı, bu nedenle şu anda başlatılamadı.  
  
 Zaman [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage'ı Kur tamamlandıktan sonra kaynaktan isteği, bu paket zaten yüklü ve başlatılmış, olası performans kaybı en az olacak şekilde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen VSPackage'ları](../../misc/managed-vspackages.md)   
 [VSPackage'ları yönetme](../../extensibility/managing-vspackages.md)   
 [MFC uygulamalarında yerelleştirilmiş kaynaklar: Uydu DLL'leri](http://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Yönetilen VSPackage'ları](../../misc/managed-vspackages.md)

