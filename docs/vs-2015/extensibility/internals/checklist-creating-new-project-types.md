---
title: 'Denetim listesi: Yeni proje türleri oluşturma | Microsoft Docs'
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
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90b48f5969a422ab9d211bb56900cf1b3b41a78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737350"
---
# <a name="checklist-creating-new-project-types"></a>Denetim Listesi: Yeni Proje Türleri Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yeni bir proje türü oluşturmak için birkaç görevi tamamlamanız gerekir. Aşağıdaki denetim listesinde, bu görevlerin bir kılavuz sağlar.  
  
1.  Yeni Proje türünüz için işlevsellik tasarlayın. Daha fazla bilgi için [proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Hangi düzenleyicileri, kod ve diğer proje öğeleri için kullanıldığını belirleyebilirsiniz. Temel veya standart düzenleyicileri kullanabilirsiniz ya da oluşturabilir ve projeye özgü düzenleyicileri kullanır. Daha fazla bilgi için [oluşturma özel düzenleyiciler ve tasarımcılar](../../extensibility/creating-custom-editors-and-designers.md) ve [nasıl yapılır: açık projeye özgü düzenleyicileri](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Proje öğelerinizi olacaktır katılım düzeyini belirlemek **sınıf görünümü** ve **Nesne Tarayıcısı**. Daha fazla bilgi için [destekleyen sembol tarama araçlarını](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Proje ve proje öğeleri için daha önce yapılan tasarım kararlarına göre yeni bir sınıf türetin.  
  
5.  Aşağıdaki proje türü bileşenler için kodu yazın:  
  
    -   Yeni proje oluşturma ve mevcut projeleri açma yönetmek için proje üreteci. Daha fazla bilgi için [oluşturma proje örnekleri tarafından kullanarak proje Fabrikalarını](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Proje hiyerarşisi ve komut işleme. Daha fazla bilgi için [derleme içinde değil: Proje türü (C++) uygulamak için HierUtil7 proje sınıfları kullanarak](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [proje modeli öğeleri](../../extensibility/internals/elements-of-a-project-model.md), [proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)ve [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Proje öğeleri yönetimi, projenize ekleme dahil olmak üzere **yeni proje** iletişim kutusu. Daha fazla bilgi için [ekleme proje ve proje öğesi şablonları](../../extensibility/internals/adding-project-and-project-item-templates.md) ve [kaydetme proje ve öğe şablonları](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Kalıcılık proje durumu ve tek tek öğeleri. Daha fazla bilgi için [açma ve kaydetme proje öğeleri](../../extensibility/internals/opening-and-saving-project-items.md). Çözüm bilgileri kalıcılığını bkz [çözümleri](../../extensibility/internals/solutions.md).  
  
    -   Özellikler penceresinde görüntülenecek bağımsız özellikleri yapılandırma. Daha fazla bilgi için [genişletme özellikleri](../../extensibility/internals/extending-properties.md).  
  
    -   Bağımlı yapılandırma özelliklerini göstermek için özellik sayfaları'nda uygulandığı şekilde proje yapılandırma özellikleri. Daha fazla bilgi için [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Dağıtım için çıktı numaralandırma. Daha fazla bilgi için [çıkış için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Proje başlangıç Hizmetleri. Daha fazla bilgi için [proje modeli öğeleri](../../extensibility/internals/elements-of-a-project-model.md) ve [proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md).  
  
    -   Nesneleri veya türetilmiş sınıflar `IDispatch`, otomasyon için kullanılabilir.  
  
    -   XML komut tablosu (.vsct) dosyaları. Daha fazla bilgi için [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Test, hata ayıklama ve başlatma, proje türü.  
  
7.  Projenizde görüntülemek **proje** sekmesinde **Başvuru Ekle** ayarlayarak iletişim kutusu `VARIANT_TRUE` değeri olarak `VSHPROPID_ShowProjInSolutionPage`. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  VSPackage yükleme için Microsoft Installer (.msi) dosyası oluşturun. Daha fazla bilgi için [yükleme VSPackage'ları ile Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [proje türü kaydetme](../../extensibility/internals/registering-a-project-type.md), ve [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Proje türleri oluşturma zamanı](../../extensibility/internals/when-to-create-project-types.md)   
 [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)

