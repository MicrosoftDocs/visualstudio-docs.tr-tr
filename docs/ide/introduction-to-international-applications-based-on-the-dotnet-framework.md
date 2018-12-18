---
title: .NET Framework Tabanlı Uluslararası Uygulamalara Giriş
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cd2a749bc96271e4ed16872f1d5c4a485c55900e
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863965"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>.NET Framework Tabanlı Uluslararası Uygulamalara Giriş

İçinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dünya çapında kullanılmaya hazır uygulama oluşturmak için iki bölümden oluşur: genelleştirme, farklı kültürleri için uyarlayabilirsiniz uygulamalar tasarlama işlemi ve yerelleştirme, kaynakların belirli bir kültür için çevirme işlemi. Uluslararası bir hedef kitle için uygulama tasarlama hakkında genel bilgi için bkz. [dünya çapında kullanılmaya hazır uygulama geliştirmek için en iyi](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps).

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Yerelleştirme modeli, hem uygulama kodunda hem de geri dönüş kaynakları içeren bir ana derlemenin oluşur; dizeler, görüntüler ve diğer nesneler için hangi uygulama ilk olarak geliştirilen dili. Yerelleştirilmiş her uygulama, uydu derlemeleri veya yalnızca yerelleştirilmiş kaynakları içeren derlemeler olacaktır. Her zaman ana derleme yerelleştirilmiş uydu derlemede bir kaynak bulunamıyorsa, geri dönüş kaynakları içerdiğinden <xref:System.Resources.ResourceManager> sonunda ana kaynağa dönülüyor, hiyerarşik bir şekilde yüklemeyi deneyecek. Kaynak geri dönüş sistemi daha ayrıntılı olarak açıklanan [kaynakların hiyerarşik organizasyonu yerelleştirme için](../ide/hierarchical-organization-of-resources-for-localization.md).

 Tüm Microsoft sözlüğü kullanmaktır dikkate almanız gereken bir yerelleştirme kaynağı ürünleri yerelleştirilmiş. Bu CSV dosyası üzerinde 12.000 İngilizce koşulları 59 farklı dilde terimlerin çevirileri içerir. Sözlüğü, ücretsiz olarak kullanılabilir [Microsoft terminoloji çevirileri](http://go.microsoft.com/fwlink/?LinkId=128146) web sayfası.

 Windows Forms uygulamaları için proje sistemi her iki geri dönüş için kaynak dosyaları oluşturabilir ve her ek kullanıcı Arabirimi kültürünü istenen. Geri dönüş kaynak dosyası ana derlemeye oluşturulmuştur ve kültüre özgü kaynak dosyaları, her UI kültürü için bir uydu derlemeler içinde yerleşik olan. Bir proje oluşturduğunuzda, kaynak dosyalarını Visual Studio XML biçimi (.resx) Ara bir ikili biçimine (.resources), ardından uydu derlemeleri içinde gömülü derlenir.

 Hem Windows Formları ve web formları için proje sistemi projenizi bir bütünleştirilmiş kod kaynak dosyası şablonu kullanarak kaynak dosyaları derleme ve kaynaklara erişim sağlar. Uydu derlemeleri ana derlemenin birlikte oluşturulur.

 Yerelleştirilmiş bir uygulama yürütüldüğünde, görünümünü iki kültüre değerlerine göre belirlenir. (A *kültür* kullanıcının dil, ortam ve kültürel ilgili kullanıcı tercihi bilgileri kümesidir.) UI kültür ayarı, hangi kaynakların yükleneceğini belirler. UI kültürü olarak ayarlandığından `UICulture` Web.config dosyaları ve sayfa yönergeleri ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> Visual Basic veya C# kod. Tarih, sayı, para birimi ve benzeri gibi değerler biçimlendirmesini kültür ayarı belirler. Kültür olarak ayarlanır `Culture` Web.config dosyaları ve sayfa yönergelerinde <xref:System.Globalization.CultureInfo.CurrentCulture%2A> Visual Basic veya C# kod.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization>
- <xref:System.Resources>
- [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)
- [Güvenlik ve Yerelleştirilmiş Yardımcı Derlemeler](../ide/security-and-localized-satellite-assemblies.md)