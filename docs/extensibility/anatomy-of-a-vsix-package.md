---
title: Bir VSIX paketinin anatomisi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1dea0fce75d83678161013baef109364842fcc46
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937739"
---
# <a name="anatomy-of-a-vsix-package"></a>Bir VSIX paketinin anatomisi
Bir VSIX paketi bir *.vsix* sınıflandırmak ve uzantıları yüklemek için bir veya daha fazla Visual Studio uzantıları, Visual Studio meta verileri ile birlikte içeren bir dosya kullanır. Meta verilerin yer alan VSIX bildirimi içinde ve *[Content_Types] .xml* dosya. Bir VSIX paketi de bir veya daha fazla içerebilir *Extension.vsixlangpack* sağlamak üzere dosyaları Kurulum metninde yerelleştirilmiş ve bağımlılıklarını yüklemek için ek VSIX paketleri içerebilir.  
  
 VSIX paket biçimi açık paketleme kuralları (OPC) standart izler. Paket ile birlikte ikili dosyalar ve Destek dosyalarını içeren bir *[Content_Types] .xml* dosyası ve bir *.vsix* bildirim dosyası. Bir VSIX paketi birden çok proje veya kendi bildirimleri olan bile birden çok paketleri çıktısını içerebilir.  
  
> [!NOTE]
>  VSIX paketlerinde dosyalarının adlarını boşluklar içermemelidir ya da devre dışı olarak Tekdüzen Kaynak Tanımlayıcıları (URI) içinde ayrılmış karakterleri tanımlanan altında [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>VSIX bildirimi  
 VSIX bildirimi uzantının yüklenmesini ve aşağıdaki VSX şeması hakkında bilgi içerir. Daha fazla bilgi için [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Bir örnek VSIX bildirimi için bkz: [PackageManifest öğesi (kök öğe, VSX şema)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 VSIX bildirimi adlandırılmalıdır `extension.vsixmanifest` zaman bunu dahil bir ^ .vsix * dosya.  
  
## <a name="the-content"></a>İçeriği  
 Bir VSIX paketi şablonları, araç kutusu öğelerini, VSPackages veya başka tür bir Visual Studio tarafından desteklenen uzantısı içerebilir.  
  
## <a name="language-packs"></a>Dil paketleri  
 Bir VSIX paketi bir kez veya daha fazla içerebilir *Extension.vsixlangpack* dosyaları yükleme sırasında yerelleştirilmiş metin sağlayın. Daha fazla bilgi için [yerelleştirme VSIX paketlerini](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Bağımlılıklar ve başvuruları  
 Bir VSIX paketi diğer VSIX paketleri başvuru olarak içerebilir. Her diğer bu paketlerin kendi VSIX bildirimi eklemeniz gerekir.  
  
 Bir kullanıcı, bağımlılıklara sahip bir uzantıyı yüklemeye çalışırsa, yükleyici, gerekli derlemeleri kullanıcı sistemde yüklü olduğunu doğrular. Gerekli derlemeleri bulunmazsa, **Uzantılar ve güncelleştirmeler** eksik derlemelerin bir listesini görüntüler.  
  
 Bir veya daha fazla uzantı bildirimi içeriyorsa, [başvuru](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) öğeleri **Uzantılar ve güncelleştirmeler** sistemde yüklü uzantıları her başvurunun bildirimi karşılaştırır ve yükler Başvurulan uzantı zaten yüklü değilse. Başvurulan uzantı önceki bir sürümü yüklüyse, yeni sürümü değiştirir.  
  
 Birden çok proje çözümde bir proje, aynı çözümdeki başka bir projeye bir başvuru içeriyorsa, proje bağımlılıklarını VSIX paketini içerir. Başvuru iç projesi için ve ardından tıklayarak bu davranışı geçersiz kılabilirsiniz **özellikleri** ayarlama penceresinde **çıktı grupları dahil vsıx'te** özelliğini `BuiltProjectOutputGroup`.  
  
 Başvurulan derlemelerden Uydu DLL'leri VSIX paketinde eklemek için Ekle `SatelliteDllsProjectOutputGroup` için **çıktı grupları dahil vsıx'te** özelliği.  
  
## <a name="installation-location"></a>Yükleme konumu  
 Yükleme sırasında **Uzantılar ve güncelleştirmeler** altında bir klasöre VSIX paketinin içeriği arar *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.  
  
 Varsayılan olarak, çünkü yalnızca geçerli kullanıcının yükleme uygular *% LocalAppData %* kullanıcıya özgü dizinidir. Ancak ayarlarsanız [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) için bildirimin öğesi `True`, uzantı altında yüklü <em>... \\</em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> ve bilgisayarın tüm kullanıcıları için kullanılabilir olacak.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 *[Content_Types] .xml* dosyayı genişletilmiş dosya türlerini tanımlayan *.vsix* dosya. Visual Studio Paket yüklemesi sırasında bu dosyayı kullanır ancak dosyayı yüklemez. Bu dosya hakkında daha fazla bilgi için bkz. [[Content_types] .xml dosyasının yapısı](the-structure-of-the-content-types-dot-xml-file.md).  
  
 A *[Content_Types] .xml* dosya açık paketleme kuralları (OPC) standart tarafından gerekli. OPC hakkında daha fazla bilgi için bkz: [OPC: verilerinizi paketleme için yeni bir standart](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) MSDN Web sitesinde.