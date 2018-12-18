---
title: Komutlar, menüler ve araç çubukları | Microsoft Docs
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
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 61
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c9641f788951e79efb392927371bb55b49ec294
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752579"
---
# <a name="commands-menus-and-toolbars"></a>Komutlar, Menüler ve Araç Çubukları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Menüleri ve araç çubuklarını, VSPackage komutlarında kullanıcıların erişimi olan. Yazdırma, bir görünümü yenileme veya yeni bir dosya oluşturmak gibi görevleri gerçekleştirmek işlevleri komutlardır. Menüleri ve araç çubuklarını komutlarınızı sunmak için uygun grafik yöntemlerdir. Genellikle, ilgili komutları birlikte aynı menü veya araç çubuğunda kümelenir.  
  
- Menüleri, genellikle bir satırda tümleşik geliştirme ortamı (IDE) veya bir araç penceresinin üst kısmındaki kümelenmiş Tek sözcüklü dizeler olarak görüntülenir. Menüler ayrıca sağ tıklama olay sonucu olarak görüntülenir ve bu bağlamda kısayol menüleri olarak adlandırılır. Tıklandığında, menüler, bir veya daha fazla komut görüntülemek için genişletin. Tıklandığında, komutları, görevleri gerçekleştirmek veya ek komutlar içeren alt menüler başlatın. Bazı iyi bilinen menü adları, dosya, düzenleme, görüntüleme ve pencere ' dir. Daha fazla bilgi için [genişletme menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).  
  
- Araç çubukları, düğmeler ve birleşik giriş kutuları, liste kutuları, metin kutuları ve menü denetleyicisi gibi başka denetimler satırlarını genellikle cihazlardır. Tüm araç çubuğu denetimleri komutları ile ilişkilidir. Araç çubuğu düğmesini tıkladığınızda ilişkilendirilmiş, komut etkin hale gelir. Araç çubuğu düğmeleri, genellikle bir yazıcıya yazdırma komutu gibi temel alınan komutlar öneren simgeleri olur. Bir açılan liste denetiminde listedeki her öğeyi başka bir komut ile ilişkilidir. Araç çubuğu düğmesi denetimi bir tarafı olduğunu ve diğer tarafında tıklandığında ek komutlar görüntüleyen bir aşağı oka olan karma bir menü denetleyicisidir. Daha fazla bilgi için [bir araç çubuğuna menü denetleyicisi ekleme](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Bir komut oluşturduğunuzda, aynı zamanda bir olay işleyicisi için oluşturmanız gerekir. Olay işleyicisi belirler komutu görünür veya etkin olduğunda, metin değiştirme olanak tanır ve komut uygun şekilde yanıt vermesini sağlar ("etkinleştirildiğinde rotaları"). Çoğu durumda, IDE kullanarak komutları işleyen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. İçindeki komutlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yerel seçim temel alınarak ve genel seçime göre en dıştaki bağlamı geçmeden en içteki komut bağlamı ile başlayarak, hiyerarşik bir şekilde rota. Ana menüye eklenen komutlar, komut dosyası için hemen kullanılabilir. Daha fazla bilgi için [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) ve [seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md).  
  
  Yeni menüleri ve araç çubuklarını tanımlamak için bir Visual Studio komut tablosu (.vsct) dosyasında açıklamanız gerekir. Visual Studio Paket şablonu hangi komutları, araç çubukları ve şablonda seçili düzenleyicileri desteklemek için gerekli öğeler birlikte, bu dosyayı oluşturur. Alternatif olarak, burada açıklanan xml şeması kullanarak kendi .vsct dosyası yazabilirsiniz: [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md).  
  
  .Vsct dosyaları ile çalışma hakkında daha fazla bilgi için bkz. [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  Bu bölümdeki konularda, komutlar, menüler ve araç çubukları Vspackage'larda nasıl çalıştığı açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Komut tablosu biçim belirtimi ayrıntılı bir açıklaması.  
  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Bir XML tabanlı sözdizimi ve derleyicisi komut tablolar için açıklar.  
  
 [Varsayılan Komut, Grup ve Araç Çubuğu Yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Önceden tanımlanmış komutları, grupları, menüleri ve araç çubukları açıklar.  
  
 [IDE Tanımlı Komutlar, Menüler ve Gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Önceden tanımlanmış menüler, komutlar ve komut grubu tarafından kullanılmak üzere yok belirtir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Komut Tasarımı](../../extensibility/internals/command-design.md)  
 Komutları tasarım açıklanmaktadır.  
  
 [Menü ve Araç Çubuğu Komutlarını En İyi Duruma Getirme](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Komutları için yönergeler sağlar.  
  
 [Komutları Kullanılabilir Yapma](../../extensibility/internals/making-commands-available.md)  
 Komutları için Visual Studio tarafından kullanılabilmesini açıklanmaktadır.  
  
 [Birlikte Çalışma Bütünleştirilmiş Kodları Kullanan Komutlar ve Menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Birlikte çalışma bütünleştirilmiş kodları kullanan komutlar uygulanacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [VSPackage’larda Komut Yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)  
 Vspackage'larda komut yönlendirme açıklar.

