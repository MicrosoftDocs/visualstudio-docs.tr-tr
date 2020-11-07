---
title: Derleme ve bildirim imzalamayı yönetme
description: Bir yazılım bileşenine küresel olarak benzersiz bir kimlik veren tanımlayıcı ad imzalama avantajları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bdd2570f94b0f5577c7c09a696906338245f77a4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351394"
---
# <a name="manage-assembly-and-manifest-signing"></a>Derleme ve bildirim imzalamayı yönetme

Tanımlayıcı ad imzalama, bir yazılım bileşenine genel olarak benzersiz bir kimlik verir. Tanımlayıcı adlar, derlemenin başka bir kişi tarafından taklit edilemez olduğunu garantilemek ve Bileşen bağımlılıkları ve yapılandırma deyimlerinin doğru bileşen ve bileşen sürümüne eşlendiğini doğrulamak için kullanılır.

Güçlü bir ad, derlemenin kimliğinden (basit metin adı, sürüm numarası ve kültür bilgileri) ve bir ortak anahtar belirteci ve dijital imzadan oluşur.

Visual Basic ve C# projelerinde derlemeleri imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

C++ projelerinde derlemeleri imzalama hakkında daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Tanımlayıcı ad imzalama, derlemenin ters mühendisine karşı koruma sağlamaz. Ters mühendisliğe karşı korunmak için bkz. [Dotfuscator topluluğu](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Varlık türleri ve imzalama

.NET derlemelerini ve uygulama bildirimlerini imzalayabilirsiniz:

- Yürütülebilir dosyalar ( *. exe* )

- Uygulama bildirimleri ( *. exe. manifest* )

- Dağıtım bildirimleri ( *. Application* )

- Paylaşılan bileşen derlemeleri ( *. dll* )

Aşağıdaki varlık türlerini imzalayın:

1. Derlemeleri genel derleme önbelleği 'ne (GAC) dağıtmak istiyorsanız.

2. ClickOnce uygulaması ve dağıtım bildirimleri. Visual Studio bu uygulamalar için varsayılan olarak imzalama imkanı sunar.

3. COM birlikte çalışabilirlik için kullanılan birincil birlikte çalışma derlemeleri. TLBIMP yardımcı programı bir COM tür kitaplığından birincil birlikte çalışma derlemesi oluştururken güçlü adlandırma uygular.

Genel olarak, yürütülebilir dosyaları imzalayamamalıdır. Kesin adlandırılmış bir bileşen, uygulamayla dağıtılan, kesin olmayan adlandırılmış bir bileşene başvuramaz. Visual Studio uygulama yürütülebilir dosyalarını imzalamaz, bunun yerine zayıf adlı yürütülebiliri işaret eden uygulama bildirimini imzalar. İmzalama, bağımlılıkları yönetmeyi daha zor hale yapabileceğinden, uygulamanıza özel bileşenleri imzamaktan kaçının.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Visual Studio 'da bir derlemeyi imzalama

Proje Özellikleri penceresinin **imzalama** sekmesini kullanarak bir uygulamayı veya bileşeni imzalayabilirseniz ( **Çözüm Gezgini** içinde proje düğümüne sağ tıklayıp **Özellikler** ' i seçin). **İmzalama** sekmesini seçin ve ardından **derlemeyi imzala** onay kutusunu seçin.

Bir anahtar dosyası belirtin. Yeni bir anahtar dosyası oluşturmayı seçerseniz, yeni anahtar dosyaları her zaman *. pfx* biçiminde oluşturulur. Yeni dosya için bir ad ve parola gerekir.

> [!WARNING]
> Başka birinin kullanmasını engellemek için anahtar dosyanızı her zaman bir parolayla korumanız gerekir. Ayrıca, sağlayıcıları veya sertifika depolarını kullanarak anahtarlarınızın güvenliğini sağlayabilirsiniz.

Ayrıca zaten oluşturmuş olduğunuz bir anahtara işaret edebilirsiniz. Anahtar oluşturma hakkında daha fazla bilgi için bkz. [genel-özel anahtar çifti oluşturma](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Yalnızca bir ortak anahtara erişiminiz varsa, anahtarın atanmasını ertelerseniz gecikme imzalamayı kullanabilirsiniz. **Yalnızca gecikmeli imzala** onay kutusunu seçerek gecikmeli imzalamayı etkinleştirin. Gecikmeli imzalanmış bir proje çalıştırılmaz ve hata ayıklayamazsınız. Ancak, seçeneği ile [Sn.exe tanımlayıcı adı aracını](/dotnet/framework/tools/sn-exe-strong-name-tool) kullanarak geliştirme sırasında doğrulamayı atlayabilirsiniz `-Vr` .

Bildirimleri imzalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini](../ide/how-to-sign-application-and-deployment-manifests.md)imzalama.

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlandırılmış derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)
- [Tanımlayıcı adlı derlemeler (C++/CLı)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
