---
title: Derleme oluşturma
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7681ad9cd109dbc8da266721d9d8382d3552eda6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062599"
---
# <a name="compile-and-build-in-visual-studio"></a>Derleme ve Visual Studio'da derleyin

Kaynak kodu derlerken, derleme altyapısı derlemeler ve yürütülebilir uygulamalar oluşturur. Genel olarak, derleme işlemi Windows, ASP.NET, mobil uygulamalar ve diğerleri gibi birçok farklı proje türlerinde çok benzer. Derleme işlemi ayrıca gibi programlama dillerini benzer C#, Visual Basic, C++ ve F#.

Kodunuzu genellikle oluşturarak hızlı bir şekilde sözdizimi, yanlış yazılmış anahtar sözcükler gibi derleme zamanı hataları belirlemek ve uyuşmazlıkları yazın. Ayrıca, algılamak ve çalışma zamanı hataları, mantık hataları ve anlamsal hataları gibi oluşturma ve kod hata ayıklama sürümlerini çalıştıran düzeltin.

Uygulamanın kaynak kodunu doğru söz dizimini içerir ve kitaplıkları, derlemeler ve diğer bileşenleri için tüm statik başvuruları çözümlemek başarılı bir derleme doğrular. Çalıştırılabilir bir uygulamaya üretilen, test edilebilirler düzgün hem de çalışması için bir [ortam hata ayıklama](../debugger/index.md) ve el ile ve otomatik testler için çeşitli [kod kalitesini doğrulamak](../test/improve-code-quality.md). Uygulamanın tam olarak test sonra müşterilerinize dağıtmak için bir yayın sürümünü derleyebilirsiniz. Bu işlem, giriş için bkz. [izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

Bir uygulama oluşturmak için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz: Visual Studio IDE, MSBuild komut satırı araçları ve Azure işlem hatları:

| Derleme yöntemi | Yararları |
| --- |--- | --- |
| IDE |-Derlemeleri hemen oluşturun ve bunları bir hata ayıklayıcıda test edin.<br />-C++ ve C# projeleri için birden çok işlemcili derlemeleri çalıştırın.<br />-Derleme sistemin farklı yönlerini özelleştirin. |
| MSBuild komut satırı| -Visual Studio yüklemeden projeleri oluşturun.<br />-Çalışma birden çok işlemcili için tüm proje türleri oluşturur.<br />-Birçok alan yapı sisteminin özelleştirin.|
| Azure işlem hatları | -Bir sürekli tümleştirme/sürekli teslim işlem hattı bir parçası olarak yapı sürecinizi otomatik hale getirin.<br />-Her derleme ile otomatik testler için geçerlidir.<br />-Yapı işlemleri için neredeyse sınırsız bulut tabanlı kaynakların paylaşmayan kullanır.<br />-Yapı iş akışını değiştirin ve ayrıntılı bir şekilde özelleştirilmiş görevleri gerçekleştirmek için yapı etkinlikleri oluşturun.|

Bu bölümdeki belgeler, daha fazla IDE tabanlı yapı işleminin ayrıntılarına gider. Diğer yöntemler hakkında daha fazla bilgi için bkz. [MSBuild](../msbuild/msbuild.md) ve [Azure işlem hatları](/azure/devops/pipelines/index?view=vsts)sırasıyla.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [derlemek ve Mac için Visual Studio'da oluşturmak](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>IDE'den oluşturmaya genel bakış

Bir proje oluşturduğunuzda, Visual Studio projeyi ve projeyi içeren çözüm derleme yapılandırmaları varsayılan oluşturulur.  Bu yapılandırmaları nasıl çözümler ve projeler dağıtılan ve derlenen tanımlar. Proje yapılandırmaları, özellikle bir hedef Platformu (örneğin, Windows veya Linux) için benzersizdir ve türlerinin (örneğin, hata ayıklama veya sürüm) oluşturun. İster ve kendi yapılandırmalarınızı gerektiği gibi oluşturabilirsiniz ancak bu yapılandırmalar düzenleyebilirsiniz.

IDE içinden yapı ilk bir giriş için bkz. [izlenecek yol: uygulama oluşturma](walkthrough-building-an-application.md).

Ardından, bkz: [oluşturma ve projeler ve çözümler Visual Studio'da Temizleme](building-and-cleaning-projects-and-solutions-in-visual-studio.md) farklı yönlerini özelleştirmeleri hakkında bilgi edinmek için işlemi yapabilirsiniz. Özelleştirmeleri içerir [çıktı dizini değiştirerek](how-to-change-the-build-output-directory.md), [derleme olayları belirtme özel](specifying-custom-build-events-in-visual-studio.md), [proje bağımlılıkları yönetmek](how-to-create-and-remove-project-dependencies.md), [yapı günlüğünü yönetme dosyaları](how-to-view-save-and-configure-build-log-files.md), ve [Derleyici uyarılarını gizleme](how-to-suppress-compiler-warnings.md).

Burada, çeşitli diğer görevleri keşfedebilirsiniz:
- [Derleme yapılandırmalarını anlama](understanding-build-configurations.md)
- [Derleme platformlarını anlama](understanding-build-platforms.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md).
- Derleme olayları belirtme [C#](how-to-specify-build-events-csharp.md) ve [Visual Basic](how-to-specify-build-events-visual-basic.md).
- [Derleme seçeneklerini ayarlama](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Paralel olarak birden çok proje derleme](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Web sitesi projeleri oluşturma (derleme)](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Derlemek ve oluşturmak (Mac için Visual Studio)](/visualstudio/mac/compiling-and-building)