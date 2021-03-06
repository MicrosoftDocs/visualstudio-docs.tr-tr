---
title: Çıkış Kümesi için Proje | Microsoft Docs
description: Her yapılandırmanın destekleyene derleme işlemleri ve çıkış öğelerinin kullanılabilir olduğu arabirimler ve yöntemler hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b718e70bac0d9e09936daf743420acc04a1c4ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899881"
---
# <a name="project-configuration-for-output"></a>Çıkış için Proje Yapılandırması
Her yapılandırma, yürütülebilir dosya veya kaynak dosyaları gibi çıkış öğeleri üreten bir dizi derleme işlemini desteklemektedir. Bu çıkış öğeleri kullanıcıya özeldir ve yürütülebilir dosyalar (.exe, .dll, .lib) ve kaynak dosyalar (.idl, .h dosyaları) gibi ilgili çıkış türlerini bağlantılı gruplara yerleştirebilirsiniz.

 Çıkış öğeleri yöntemler aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> kullanılabilir ve yöntemlerle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> numaralandırabilirsiniz. Çıkış öğelerini gruplatırken projenizin arabirimini de uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> gerekir.

 uygulanarak geliştirilen yapı, `IVsOutputGroup` projelerin çıkışları kullanıma göre gruplamasını sağlar. Örneğin, bir DLL kendi program veritabanı (PDB) ile gruplandı olabilir.

> [!NOTE]
> Bir PDB dosyası hata ayıklama bilgilerini içerir ve hata ayıklama bilgileri oluşturulurken 'Hata Ayıklama Bilgisi Oluştur' seçeneği belirtildi .dll veya .exe. .pdb dosyası genellikle yalnızca Proje yapılandırmasında hata ayıklama için oluşturulur.

 Bir grup içinde yer alan çıkışların sayısı yapılandırmadan yapılandırmaya farklılık gösterse bile proje, desteklediği her yapılandırma için aynı sayıda grup geri dönmektedir. Örneğin, proje Matt'in DLL'si Hata ayıklama mattd.dll'da mattd.pdb ve matd.pdb'i içerebilir, ancak yalnızca Perakende yapılandırmasına matt.dll dahil olabilir.

 Gruplarda ayrıca kurallı ad, görünen ad ve grup bilgileri gibi yapılandırmadan proje içindeki yapılandırmaya kadar aynı tanımlayıcı bilgileri vardır. Bu tutarlılık, yapılandırmalar değişse bile dağıtım ve paketlemenin çalışmaya devam eder.

 Grupların ayrıca paketleme kısayollarının anlamlı bir şeyi işaret etmek için önemli bir çıkışı da olabilir. Herhangi bir grup, bir yapılandırmada boş olabilir, bu nedenle bir grubun boyutuyla ilgili varsayımda bulunulamama gerekir. Herhangi bir yapılandırmada her grubun boyutu (çıkış sayısı), aynı yapılandırmada yer alan başka bir grubun boyutundan farklı olabilir. Başka bir yapılandırmada aynı grubun boyutundan da farklı olabilir.

 ![Çıkış Grupları grafiği](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Çıkış grupları

 Arabirimin birincil kullanımı, yönetim nesnelerini derleme, dağıtma ve hata ayıklama erişimi sağlamak ve projelerin çıkışları <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> grup kullanma özgürlüğü sağlamaktır. Bu arabirimin kullanımı hakkında daha fazla bilgi için bkz. [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 Önceki diyagramda Grup Oluşturma, yapılandırmalar (bD.exe veya b.exe) genelinde önemli bir çıkışa sahiptir. Bu nedenle kullanıcı, Yerleşik kısayolu oluşturabilir ve dağıtılan yapılandırmadan bağımsız olarak kısayolun çalışa bilebilirsiniz. Grup Kaynağının bir anahtar çıkışı yok, bu nedenle kullanıcı bu çıkışa bir kısayol oluşturamaz. Yerleşik Hata Ayıklama Grubu önemli bir çıkışa sahipse ama Retail Group Built yoksa, bu yanlış bir uygulama olur. Ardından, herhangi bir yapılandırmada çıkış içeren bir grup varsa ve sonuç olarak anahtar dosyası yoksa, bu grupla çıkış içeren diğer yapılandırmalarda anahtar dosyaları olamaz. Yükleyici düzenleyicileri kurallı adların ve grupların görünen adlarının yanı sıra bir anahtar dosyanın varlığından yapılandırmalara göre değişiklik olmadığını varsaymaktadır.

 Projesinde paket veya dağıtım yapmak istemeyen bir proje varsa, bu çıkışı bir gruba `IVsOutputGroup` koymamanın yeterli olduğunu unutmayın. Yine de, gruplamadan bağımsız olarak bir yapılandırmanın tüm çıkışlarını döndüren yöntemi uygulanarak çıkış <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> normal şekilde numaralandırıldı.

 Daha fazla bilgi için, projeleri için `IVsOutputGroup` MPF'deki Özel Proje [örneğinde uygulamasına bakın.](https://github.com/tunnelvisionlabs/MPFProj10)

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
