---
title: Yerelleştirme araçları
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c6934c816574796d59f978c3d2f37f590cf578
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565129"
---
# <a name="develop-globalized-and-localized-apps"></a>Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirin

Visual Studio, [.net](/dotnet/standard/globalization-localization/)' te yerleşik hizmetlerden yararlanarak uluslararası bir hedef kitle için geliştirmeyi kolaylaştırır.

Örneğin, Windows Forms uygulamalar için proje sistemi hem geri dönüş Kullanıcı arabirimi kültürü hem de her ek kullanıcı arabirimi kültürü için kaynak dosyaları oluşturabilir. Visual Studio 'da bir proje oluşturduğunuzda, kaynak dosyaları Visual Studio XML biçiminden (. resx), daha sonra uydu derlemelerine gömülü bir ara ikili biçimi (. resources) ile derlenir. Daha fazla bilgi için bkz. [Visual Studio 'Da kaynak dosyaları](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) ve [Masaüstü uygulamaları Için uydu derlemeleri oluşturma](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Çift yönlü diller

Arapça ve Ibranice gibi sağdan sola yazılan dillerde metni doğru şekilde görüntüleyen uygulamalar oluşturmak için Visual Studio 'Yu kullanabilirsiniz. Bazı özellikler için, yalnızca özellikleri ayarlayabilirsiniz. Diğer durumlarda, koddaki özellikleri uygulamanız gerekir.

> [!NOTE]
> Çift yönlü dilleri girip görüntülemesi için, uygun dille yapılandırılmış bir Windows sürümüyle çalışmanız gerekir. Bu, uygun dil paketinin yüklü olduğu bir Windows Ingilizce sürümü ya da Windows 'un uygun şekilde yerelleştirilmiş sürümü olabilir.

### <a name="apps-that-support-bidirectional-languages"></a>Çift yönlü dilleri destekleyen uygulamalar

- Windows uygulamaları

   Çift yönlü metin, sağdan sola okuma düzeni ve yansıtma (pencere, menü ve iletişim kutularının düzenini tersine çevirme) için destek içeren tam çift yönlü uygulamalar oluşturabilirsiniz. Yansıtma haricinde, bu özellikler varsayılan olarak veya özellik ayarları olarak kullanılabilir. Yansıtma, ileti kutuları gibi bazı özellikler için kendiliğinden desteklenir. Ancak, diğer durumlarda kodda yansıtma uygulamanız gerekir. Daha fazla bilgi için bkz. [Windows Forms uygulamalar için çift yönlü destek](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Web uygulamaları

   Web Hizmetleri, çift yönlü dilleri içeren uygulamalar için uygun hale getirerek UTF-8 ve Unicode metin gönderip almayı destekler. Web istemcisi uygulamaları, Kullanıcı arabirimi için tarayıcıları kullanır, bu nedenle bir Web uygulamasında çift yönlü destek derecesi, kullanıcı tarayıcısının bu çift yönlü özellikleri ne kadar iyi desteklediğine bağlıdır. Visual Studio 'da Arapça veya Ibranice metin, sağdan sola okuma düzeni, dosya kodlama ve yerel kültür ayarları desteğiyle uygulamalar oluşturabilirsiniz. Daha fazla bilgi için bkz. [ASP.NET Web uygulamaları Için çift yönlü destek](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

> [!NOTE]
> Konsol uygulamaları çift yönlü diller için metin desteği içermez. Bu, Windows 'un konsol uygulamalarıyla nasıl çalıştığı hakkında bir sonucudur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da çift yönlü diller için destek](use-bidirectional-languages.md)
- [.NET uygulamalarını globalize ve yerelleştirin](/dotnet/standard/globalization-localization/)
- [.NET uygulamalarındaki kaynaklar](/dotnet/framework/resources/)
