---
title: Proje çıkışı için yapılandırma | Microsoft Docs
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
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c23f9210175b848bfdf3ddab56776092e39212c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740895"
---
# <a name="project-configuration-for-output"></a>Çıkış için Proje Yapılandırması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Her yapılandırma bir dizi yürütülebilir dosyası ya da kaynak dosyaları gibi çıkış öğeleri oluşturan yapı işlemlerini destekler. Bu çıkış öğeleri kullanıcıya özeldir ve yürütülebilir dosyalar (.exe, .dll, .lib) ve kaynak dosyaları (.idl, .h dosyaları) gibi bir çıkış ilgili türü bağlantı gruplardaki yerleştirilebilir.  
  
 Çıktı öğeleri kullanılabilir hale aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> yöntemleri ve ile numaralandırılmış <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> yöntemleri. Çıktı öğeleri için gruplandırma istediğinizde projenizin de uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> arabirimi.  
  
 Yapı geliştirilen uygulayarak `IVsOutputGroup` projeleri kullanım göre grup çıkışlarına izin verir. Örneğin, bir DLL, program veritabanı (PDB) ile gruplandırılmış olabilir.  
  
> [!NOTE]
>  Bir PDB dosyası hata ayıklama bilgileri içerir ve .dll veya .exe oluştururken 'Hata ayıklama bilgisi Oluştur' seçeneği belirtildiğinde oluşturulur. .Pdb dosyası, genellikle yalnızca hata ayıklama proje yapılandırması için oluşturulur.  
  
 Bir gruptaki çıktı sayısı yapılandırma yapılandırması değişebilir olsa bile Proje grupları desteklediği her bir yapılandırma için aynı sayıda döndürmesi gerekir. Örneğin, projenin Matt DLL mattd.dll ve mattd.pdb hata ayıklama yapılandırmasını da dahil, ancak yalnızca matt.dll perakende yapılandırmasında dahildir.  
  
 Gruplar aynı tanımlayıcı bilgileri, kurallı ad, görünen ad ve grup bilgilerini gibi içinde bir proje yapılandırması başka bir yapılandırmayı da sahip. Bu tutarlılık, dağıtım ve yapılandırmaları değiştirseniz bile çalışmaya devam etmek için paketleme sağlar.  
  
 Grupları, anlamlı işaret edecek şekilde paketleme kısayolları sağlayan anahtar bir çıktı da olabilir. Bir grubu boyutu hakkında hiçbir varsayım yapılması gereken şekilde herhangi bir grubu belirli bir yapılandırmada boş olabilir. Her grupta herhangi bir yapılandırma boyutu (çıkışlar sayısı) aynı yapılandırmayı başka bir grupta boyutunu farklı olabilir. Ayrıca başka bir yapılandırma aynı grupta boyutunu farklı olabilir.  
  
 ![Çıkış grupları grafiği](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Çıkış grupları  
  
 Birincil kullanım alanının <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> oluşturmanızı, dağıtmanızı ve yönetim nesneleri hata ayıklama ve grup çıkışları özgürlüğü projelerin kullanmasına izin vermek için erişim sağlamak için arabirimidir. Bu arabirim kullanımı hakkında daha fazla bilgi için bkz. [proje yapılandırması nesnesi](../../extensibility/internals/project-configuration-object.md).  
  
 Önceki diyagramda, Grup oluşturulan (bD.exe veya b.exe) yapılandırmalar arasında bu nedenle çıktı bir anahtara sahip kullanıcı, yerleşik bir kısayol oluşturun ve kısayol dağıtılan yapılandırma bağımsız olarak çalışacağını bildirin. Kaynak grubu çıkış, bir anahtar olmadığından, kullanıcı bir kısayol oluşturamaz. Hata ayıklama grubu oluşturulmuş bir anahtar çıktı olsa da, perakende yerleşik grup yok, hatalı bir uygulama olacaktır. Herhangi bir yapılandırma hiç çıkış içeren bir grubu varsa, daha sonra takip eden ve sonuç olarak, anahtar dosyası ve çıktılar içeren diğer yapılandırmalar o grubun anahtar dosyaları olamaz. Yükleyici düzenleyicileri kurallı adları ve grupların görünen adlarını yanı sıra, bir anahtar dosyası varlığını değiştirmeyin tabanlı yapılandırmaları varsayılır.  
  
 Bir proje varsa unutmayın bir `IVsOutputGroup` paketini veya dağıtmak istediğinizi değil, bunu bu çıkışı bir gruba yerleştirmek değil yeterlidir. Çıktı hala normalde uygulayarak numaralandırılabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> bir yapılandırmasının çıktı gruplandırma bağımsız olarak tüm döndüren yöntem.  
  
 Daha fazla bilgi için bkz: `IVsOutputGroup` özel Proje örneğinde [MPF projeleri için](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md)   
 [Derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)   
 [Proje yapılandırması nesnesi](../../extensibility/internals/project-configuration-object.md)   
 [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)

