---
title: Vspackage'lardaki kaynaklar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4de310a9b1c0cfdfcbbf2855d3e371e118be8bdf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856294"
---
# <a name="resources-in-vspackages"></a>VSPackage’lardaki Kaynaklar
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
  
  Kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> belirtmek için özniteliği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yönetilen kaynaklar kullanılabilir.  
  
  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
  Ayarı <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> bu şekilde bildiren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yönetilmeyen Uydu DLL'leri, kaynaklar için örneğin, kullanarak ararken sayılmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Varsa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aynı kaynak Kimliğine sahip iki veya daha fazla kaynak karşılaştığında bulduğu ilk kaynak kullanır.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mümkün olduğunda VSPackages yüklenmesini gecikmeler. VSPackage'ı CTO dosya ekleme bir sonuç [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birleştirilmiş komut tablosu oluşturduğunda, Kurulum sırasında tüm bu tür bellek Vspackage'larda yüklemeniz gerekir. Kaynaklar meta verileri inceleyerek VSPackage içinde kod çalıştırmadan VSPackage ayıklanabilir. VSPackage'ı en düşük performans kaybı, bu nedenle şu anda başlatılamadı.  
  
 Zaman [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ı Kur tamamlandıktan sonra kaynaktan isteği, bu paket zaten yüklü ve başlatılmış, olası performans kaybı en az olacak şekilde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage'ları yönetme](../../extensibility/managing-vspackages.md)   
 [MFC Uygulamalarında Yerelleştirilmiş Kaynaklar: Uydu DLL'leri](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
