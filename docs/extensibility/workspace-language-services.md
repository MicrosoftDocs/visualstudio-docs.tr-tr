---
title: Çalışma alanları ve Visual Studio'da dil Hizmetleri | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: be9fb8c1e3ae363898e0438bdd1ec34c9fd23727
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735457"
---
# <a name="workspaces-and-language-services"></a>Çalışma alanları ve dil Hizmetleri

Dil hizmetleri sağlayabilir [Klasör Aç](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) kullanıcılar aynı zengin dil özellikleri oldukları için kullanılan çözüm ve projelerle çalışırken. Dil hizmeti kendi kendine etkinleştirme "gevşek dosyası" Bu dil hizmeti söz dizimi vurgulama için sınırlı olmasına rağmen dosya uzantısı veya açılan bir belge içeriğini göre. Ek bilgiler, kaynak kodu düzenleme/gözden geçirirken daha zengin bir deneyim sağlamak için gereklidir. Her dil hizmeti, bir belge için bu ek bağlamsal veriler ile başlatma için kendi API vardır. Bu, genellikle hem dil hizmeti hem de yapı sistemi sıkı şekilde bağlı bir proje sistemi tarafından yönetilir.

## <a name="initialization"></a>Başlatma

İçinde bir [çalışma](workspaces.md), dil Hizmetleri tarafından başlatılan bir <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> yalnızca o dil hizmetinde uzmanlaşmış ve hiçbir derleme yazma bilir genişletme noktası. Bu şekilde, bir dil hizmet sahibi uzantı kaç desenleri bağımsız olarak mevcut klasörleri ve dosyaları, derleyici derleme sırasında (örneğin MSBuild, derleme görevleri dosyalarını, vb.) çalıştırmak için tek açık klasör koruyabilirsiniz. Diskte bir dosya bağlamı oluşturulduğu dosyaları değiştirilse ve dosya bağlam yenilendiğinde, dil hizmeti sağlayıcısı dosya bağlamları güncelleştirilmiş kümesini bildirilir. Dil hizmeti sağlayıcısı, ardından kendi modelini güncelleştirebilirsiniz.

Bir belge Düzenleyicisi'nde açıldığında, Visual Studio yalnızca eşleşen bir dosya bağlam sağlayıcısına bulunabilir dosya bağlam türleri gerektiren hizmet sağlayıcıları dil dikkate alır. Ardından dosya bağlamı eşleşen sağlayıcılardan seçili dil hizmeti sağlayıcısına arabimini `ILanguageServiceProvider.InitializeAsync`. Dil hizmeti sağlayıcısı ile dosya bağlam verileri dil hizmet sağlayıcısının bir uygulama ayrıntısı olduğunu, ancak beklenen kullanıcı deneyimi, daha zengin bir dil hizmeti olan yapar, belge açılır.

## <a name="using-ilanguageserviceprovider"></a>ILanguageServiceProvider kullanma

Dil hizmeti ile bir dosya bağlamı oluşturulduğunda bildirilecek bir `ContextType` birini eşleşen `SupportedContextTypes` değerlerini dil server dışarı aktarma öznitelik.

Dil hizmeti desteklemek için bir uzantı gerekir:

- Benzersiz bir `Guid`. Bunun için kullanılacak `SupportedContextTypes` öznitelik bağımsız değişkenleri ve bir `FileContext` nesne.
- Dil dosyası içeriği
  - Sağlayıcı üreteci
    - `ExportFileContextProviderAttribute` Yukarıda özniteliği benzersiz olarak oluşturulan `Guid` içinde `SupportedContextTypes`
    - Uygulayan `IWorkspaceProviderFactory<IFileContextProvider>`
  - Sağlayıcı uygulaması `IFileContextProvider.GetContextsForFileAsync`
    - Yeni bir oluşturmak `FileContext` ile `contextType` oluşturucu bağımsız değişkeni olarak benzersiz bir şekilde oluşturulan `Guid`
    - Kullanım `Context` özelliği `FileContext` ek veriler vermek için `ILanguageServiceProvider`
- Dil hizmeti
  - Sağlayıcı üreteci
    - `ExportLanguageServiceProvider` Yukarıda özniteliği benzersiz olarak oluşturulan `Guid` içinde `SupportedContextTypes`
    - Uygulayan `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Sağlayıcı
    - Uygulayan `ILanguageServiceProvider`
    - Kullanım `ILanguageServiceProvider.InitializeAsync` bir dosya açıldığında, sağlanan bağımsız değişkenler için dil hizmetlerini etkinleştirmek için
    - Kullanım `ILanguageServiceProvider.UninitializeAsync` sağlanan bağımsız değişkenler için dil Hizmetleri bir dosya kapatıldığında devre dışı bırakmak için

>[!WARNING]
>`ILanguageServiceProvider` Yöntemleri çalışma alanı ana iş parçacığı tarafından çağrılacak. UI gecikmelerine neden önlemek için farklı bir iş parçacığında iş planlama göz önünde bulundurun.

## <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

`Microsoft.VisualStudio.Workspace.*` API'ler tek yolu, açık klasördeki dil hizmetini etkinleştirme dahil değildir. Başka bir seçenek, bir dil sunucu kullanmaktır. Hakkında daha fazla bilgi için okuma [dil sunucusu Protokolü](language-server-protocol.md).

## <a name="related-interfaces"></a>İlgili arabirimler

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> dosya türleri eşleşen bir dosya açıldığında veya kapalı düzenlemesi için çağrılır.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanı derleme](workspace-build.md) -Klasör Aç destekler MSBuild ve derleme görevleri dosyalarını gibi sistemleri oluşturun. 