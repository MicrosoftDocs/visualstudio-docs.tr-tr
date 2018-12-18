---
title: Mac için Visual Studio ile tanışın
description: Bu makale, Mac için Visual Studio özelliklerini tanıtır
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 10b27c26fcef622687b64f225dd04ae966f43cd5
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895684"
---
# <a name="introducing-visual-studio-for-mac"></a>Mac için Visual Studio ile tanışın

Mac için Visual Studio mobil, masaüstü ve web uygulamaları oluşturmak için bir modern, sofistike birçok özelliği bir ıde'dir. Bu geliştirme aşağıdaki türlerini destekler:

* .NET ile mobil: Android, iOS, tvOS, watchOS
* Mac Masaüstü uygulamaları
* .NET core uygulamaları
* ASP.NET Core web uygulamaları
* Platformlar arası Unity oyunları

Bu, hata ayıklama, iOS, Mac ve Android ile yerel platform tümleştirme, zengin bir düzenleyici gibi özellikler içerir ve tümleşik kaynak denetimi.

Bu makale, Mac için Visual Studio çeşitli bölümlerini araştırmalarını ve platformlar arası uygulamalar oluşturmak için güçlü bir araç sağlayan özellikler sunar.

> [!TIP]
> Visual Studio 2019 Mac preview için test etmek için kullanıma sunulmuştur. Aşağıdaki adımları [yükleme yönergeleri](install-preview.md) atın [IDE Turu](ide-tour.md).

## <a name="installation"></a>Yükleme

Bağlantısındaki [yükleme](install-preview.md) indirin ve Mac için Visual Studio Yükleme Kılavuzu

## <a name="language-support"></a>Dil desteği

Mac için Visual Studio geliştirme destekler C# ve F#, varsayılan olarak.

### <a name="c"></a>C#

C# Mac için Visual Studio'da platformlar arası uygulamalar oluşturmak için en yaygın olarak kullanılan dildir IDE, tüm C# 7 özellikleri için tam destek sunar.

### <a name="f"></a>F#

F#bir türü kesin belirlenmiş işlevsel programlama dili, .NET üzerinde çalışacak şekilde tasarlanmıştır. Android, Mac ve iOS, Mac kullanıcıları için Visual Studio için bir programlama dili olarak kullanılabilir. Kullanma hakkında daha fazla bilgi için F# dilde oluşturulmuş örnekleri görmek için ziyaret edin [ F# ](https://developer.xamarin.com/guides/cross-platform/fsharp/) Kılavuzlar.

## <a name="platform-support"></a>Platform desteği

## <a name="net-core"></a>.NET Core

[.NET core](https://www.microsoft.com/net/core#macos) Windows, Linux ve Mac üzerinde çalışan uygulamalar oluşturmak için bir platform Mac için Visual Studio yükleme, oluşturma, çalıştırma ve hata ayıklama .NET Core projeleri için destek sunmaktadır. 

.NET Core projelerini çalıştırmak için .NET Core SDK'sını karşıdan yüklenip.

.NET Core desteği şunları içerir:

* C# ve F# IntelliSense.
* Konsol, kitaplık ve web uygulamaları için .NET Core proje şablonları.
* Kesme noktaları, çağrı yığını ve izleme penceresi gibi özellikler de dahil olmak üzere tam hata ayıklama desteği.
* NuGet PackageReferences ve MSBuild tabanlı geri yükleme.
* Tümleşik birim testleri çalıştırma ve hata ayıklama desteği ile .NET Core SDK'sı ile birlikte Visual Studio Test platformu test eder.
* Eski project.json biçiminden geçiş.

Başlamak için ASP.NET Core web uygulamalarına göz denetleyin [uygulamalı laboratuvarı](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="xamarin"></a>Xamarin

[Xamarin](https://developer.xamarin.com/) için birinci sınıf destekle Android, macOS, iOS, tvOS ve watchOS için zengin yerel deneyimler geliştirebilirsiniz. Xamarin.Forms platformlar arası uygulamaları, yerel işlevselliğe erişimi sınırlamadan Android, iOS ve macOS arasında XAML tabanlı UI kodunu paylaşmanıza yardımcı olur.

Başlamak için mobil uygulamalar denetleyin [uygulamalı laboratuvarı](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started).

### <a name="android"></a>Android

Visual Studio tümleşik, kendi Android SDK yöneticisini sahiptir.

Android uygulamaları için Mac için Visual Studio Android ile çalışan kendi Tasarımcısı içerir `.axml` görsel olarak kullanıcı arabirimleri oluşturmak için dosyaları. Mac için Visual Studio bu dosyalar aşağıdaki görüntüde gösterildiği gibi Android Tasarımcısı'nda açılır:

![Android kullanıcı Arabirimi Tasarımcısı](media/intro-image31.png)

Android Designer hakkında daha fazla bilgi için bkz. [Tasarımcısı genel bakış](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview) belge.

### <a name="ios"></a>iOS

İOS Designer, Mac için Visual Studio'yla tamamen tümleşiktir ve .xib ve iOS, tvOS ve WatchOS kullanıcı arabirimleri ve geçişleri oluşturmak için görsel taslak dosyalarını görsel düzenleme sağlar. Olayları işleme için sezgisel bir yaklaşım kullanarak araç ve tasarım yüzeyine arasında sürükle ve bırak işlevini kullanarak tüm kullanıcı arabirimi oluşturulabilir. İOS Tasarımcısı'nı da destekler [özel denetimler](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) avantajını tasarım zamanı işleme ile.

![iOS görsel taslak Tasarımcısı](media/intro-image30.png)

İOS Designer'ı kullanma hakkında daha fazla bilgi için bkz. [Tasarımcısı](https://developer.xamarin.com/guides/ios/user_interface/designer) belgeleri.

### <a name="mac"></a>Mac

Xamarin güzel Mac uygulamaları oluşturmanızı sağlayan yerel Mac API bağlantıları sağlar.

Mac için Visual Studio ile Mac uygulamaları yazma ile ilgili daha fazla bilgi için [Xamarin.Mac](https://developer.xamarin.com/guides/#mac) belgeleri.

## <a name="gaming"></a>Oyun

Mac için Visual Studio, platformlar arası 5.6.1 Unity ile oyun geliştirme için destek sağlar.

Başlamak için Unity denetleyin [uygulamalı laboratuvarı](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started).

## <a name="enterprise-features"></a>Kurumsal özellikler

> [!Note]
> Bu ürün yalnızca Visual Studio Enterprise aboneliği ile kullanılabilir.

### <a name="profiler"></a>Profil Oluşturucu

Xamarin Profiler, profil oluşturma için üç Gereçleri kullanılabilir sahiptir. [Xamarin Profiler giriş](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) Kılavuzu ne bu araçları ölçün ve bunlar uygulamanızı nasıl analiz inceler ve her ekranda görüntülenen verileri anlamını açıklar.

### <a name="inspector"></a>Denetçi

Xamarin Inspector'ı etkileşimli bir C# konsol kullanıcı araçlarıyla sağlar. Bu bir hata ayıklama veya tanılama Yardımcısı belgelendirme aracı veya bir deneme aracı olarak öğretim bir aracı olarak Canlı uygulamaları İnceleme olduğunda kullanılabilir.

![Xamarin Inspector](media/intro-inspector.png)

Bu iş akışı hata ayıklama (Android, iOS, Mac ve Windows) çeşitli programlama platformu hedefleyin ve, IDE tümleştirme bir zengin C# Konsolu sağlayan bir tek başına uygulamasına oluşur. 

Daha fazla bilgi için [Xamarin Inspector'ı](https://developer.xamarin.com/guides/cross-platform/inspector/) Kılavuzu.

## <a name="next-steps"></a>Sonraki adımlar

* **Turu alma** - Mac için Visual Studio'da büyük özelliklerin çoğunu özetini almak için Mac için Visual Studio bkz [IDE Turu](ide-tour.md).
* **Ayarlanan** - indirin ve Visual Studio'yu yüklemek için bkz: hakkında bilgi almak için [yükleme](installation.md) Kılavuzu.
* **Xamarin eğitim** - Xamarin ile kod geliştirin, Xamarin için Git hakkında daha fazla bilgi edinmek için [Geliştirici Merkezi](https://developer.xamarin.com).
* **Videoları** - Mac için diğer özellikler ve Visual Studio yönleri hakkında daha fazla bilgi edinmek için videoları kontrol [Xamarin University](https://university.xamarin.com) Web sitesi.
* **Uygulamalı laboratuvarlar** - Mac için Visual Studio'ya dahil çeşitli iş yükleri ile çalışmaya başlamak için kullanıma [uygulamalı laboratuvarlara](https://github.com/Microsoft/vs4mac-labs).
