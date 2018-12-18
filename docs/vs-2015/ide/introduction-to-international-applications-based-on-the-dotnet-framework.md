---
title: .NET Framework tabanlı Uluslararası uygulamalara giriş | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d1539d832b67a160e29b22b71066f72609e35b8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270048"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>.NET Framework Tabanlı Uluslararası Uygulamalara Giriş
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dünya çapında kullanılmaya hazır uygulama oluşturmak için iki bölümden oluşur: genelleştirme, farklı kültürleri için uyarlayabilirsiniz uygulamalar tasarlama işlemi ve yerelleştirme, kaynakların belirli bir kültür için çevirme işlemi. Uluslararası bir hedef kitle için uygulama tasarlama hakkında genel bilgi için bkz. [dünya çapında kullanılmaya hazır uygulama geliştirmek için en iyi](http://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).  
  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Yerelleştirme modeli, hem uygulama kodunda hem de geri dönüş kaynakları içeren bir ana derlemenin oluşur; dizeler, görüntüler ve diğer nesneler için hangi uygulama ilk olarak geliştirilen dili. Yerelleştirilmiş her uygulama, uydu derlemeleri veya yalnızca yerelleştirilmiş kaynakları içeren derlemeler olacaktır. Her zaman ana derleme yerelleştirilmiş uydu derlemede bir kaynak bulunamıyorsa, geri dönüş kaynakları içerdiğinden <xref:System.Resources.ResourceManager> sonunda ana kaynağa dönülüyor, hiyerarşik bir şekilde yüklemeyi deneyecek. Kaynak geri dönüş sistemi daha ayrıntılı olarak açıklanan [kaynakların hiyerarşik organizasyonu yerelleştirme için](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Tüm Microsoft sözlüğü kullanmaktır dikkate almanız gereken bir yerelleştirme kaynağı ürünleri yerelleştirilmiş. Bu CSV dosyası üzerinde 12.000 İngilizce koşulları 59 farklı dilde terimlerin çevirileri içerir. Sözlüğü, ücretsiz olarak kullanılabilir [Microsoft terminoloji çevirileri](http://go.microsoft.com/fwlink/?LinkId=128146) Web sayfası.  
  
 Windows Forms uygulamaları için proje sistemi her iki geri dönüş için kaynak dosyaları oluşturabilir ve her ek kullanıcı Arabirimi kültürünü istenen. Geri dönüş kaynak dosyası ana derlemeye oluşturulmuştur ve kültüre özgü kaynak dosyaları, her UI kültürü için bir uydu derlemeler içinde yerleşik olan. Bir proje oluşturduğunuzda, kaynak dosyalarını Visual Studio XML biçimi (.resx) Ara bir ikili biçimine (.resources), ardından uydu derlemeleri içinde gömülü derlenir.  
  
 Hem Windows Formları ve Web formları için proje sistemi projenizi bir bütünleştirilmiş kod kaynak dosyası şablonu kullanarak kaynak dosyaları derleme ve kaynaklara erişim sağlar. Uydu derlemeleri ana derlemenin birlikte oluşturulur.  
  
 Yerelleştirilmiş bir uygulama yürütüldüğünde, görünümünü iki kültüre değerlerine göre belirlenir. (A *kültür* kullanıcının dil, ortam ve kültürel ilgili kullanıcı tercihi bilgileri kümesidir.) UI kültür ayarı, hangi kaynakların yükleneceğini belirler. UI kültürü olarak ayarlandığından `UICulture` Web.config dosyaları ve sayfa yönergeleri ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> Visual Basic veya Visual C# kod. Tarih, sayı, para birimi ve benzeri gibi değerler biçimlendirmesini kültür ayarı belirler. Kültür olarak ayarlanır `Culture` Web.config dosyaları ve sayfa yönergelerinde <xref:System.Globalization.CultureInfo.CurrentCulture%2A> Visual Basic veya Visual C# kod.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Uygulamaları Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)   
 [Güvenlik ve Yerelleştirilmiş Yardımcı Derlemeler](../ide/security-and-localized-satellite-assemblies.md)

