---
title: Ayarlar Sayfası, Proje Tasarımcısı
ms.date: 06/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c0f7b47b56522f5c4aeef0054e6b7b52434ff87
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "35609966"
---
# <a name="settings-page-project-designer"></a>Ayarlar sayfası, Proje Tasarımcısı

Kullanım **ayarları** projenin uygulama ayarlarını belirlemek için Proje Tasarımcısı'nın sayfa. Uygulama ayarlarını depolamak ve özellik ayarlarını ve diğer bilgileri uygulamanız için dinamik olarak almak etkinleştirin. Özel uygulama ve bir istemci bilgisayarda kullanıcı tercihlerini korumak da sağlıyor. Daha fazla bilgi için [uygulama ayarlarını yönetme](../managing-application-settings-dotnet.md).

Erişim için **ayarları** sayfasında, içinde bir proje düğümü seçin **Çözüm Gezgini**ve ardından **proje** > **özellikleri**. Proje Tasarımcısı göründüğünde seçin **ayarları** sekmesi.

## <a name="header-bar"></a>Başlık çubuğu

Üst kısmındaki başlık çubuğundaki **ayarları** sayfası çeşitli denetimler içerir:

**Eşitleme**

**Eşitleme** uygulamanın çalışma zamanında veya çalışma zamanında tanımlanan varsayılan değerlerine hata ayıklama sırasında kullandığı kullanıcı kapsamlı ayarları geri yüklenir. Uygulamaya özgü dosyaları verileri geri yüklemek için çalışma zamanı kaldırın diskten, proje verilerden oluşturulur.

**Yük Web ayarları**

**Web ayarları yük** görüntüler bir **oturum açma** yük kimliği doğrulanmış bir kullanıcı için ya da anonim kullanıcılar için ayarları olanak tanıyan iletişim kutusu. Bu düğme yalnızca, istemci uygulama hizmetleri üzerinde etkinleştirdiğinizde etkin **Hizmetleri** sayfasında ve belirtilen bir **hizmet konumu Web ayarları**.

**Kodu Görüntüle**

C# projeleri için **kodu görüntüle** düğmesini etkinleştirir, kod içinde görüntülemek *Staticcontenthosting.Web* dosya. Bu dosya tanımlar `Settings` üzerinde belirli olayları işlemenizi sağlar sınıfını `Settings` nesne. Visual Basic dışındaki dillerde, açıkça çağırmalısınız `Save` kullanıcı ayarlarını korumak için bu sarmalayıcı sınıfının yöntemi. Genellikle bunu **kapatma** olay işleyicisi ana formu. Aşağıdaki çağrı örneğidir `Save` yöntemi:

```csharp
Properties.Settings.Default.Save();
```

Visual Basic projeleri için **kodu görüntüle** düğmesini etkinleştirir, kod içinde görüntülemek *Settings.vb* dosya. Bu dosya tanımlar `MySettings` üzerinde belirli olayları işlemenizi sağlar sınıfını `My.Settings` nesne. Kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi için `My.Settings` nesne, bkz: [erişim uygulama ayarları](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Uygulama ayarlarına erişme hakkında daha fazla bilgi için bkz. [Windows Forms için uygulama ayarları](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Erişim değiştiricisi**

**Erişim değiştiricisi** düğmeye erişim düzeyini belirtir `Properties.Settings` (C# ' de) veya `My.Settings` (Visual Basic'te) yardımcı olan sınıflar Visual Studio oluşturur *Settings.Designer.cs* veya *Settings.Designer.vb*.

Visual C# projeleri için erişim değiştiricisi olabilir **dahili** veya **genel**.

Visual Basic projeleri için erişim değiştiricisi olabilir **arkadaş** veya **genel**.

Varsayılan ayardır **dahili** C# ve **arkadaş** Visual Basic'te. Visual Studio'nun oluşturduğu yardımcı sınıfları olarak ne zaman **dahili** veya **arkadaş**, yürütülebilir (*.exe*) uygulamaları, eklenen ayarlarını ve kaynaklar erişemiyor sınıf kitaplıkları (*.dll* dosyaları). Kaynaklar ve bir sınıf kitaplığı ayarlarını paylaşmak varsa, erişim değiştiricisi kümesine **genel**.

Ayarları yardımcı sınıfları hakkında daha fazla bilgi için bkz: [uygulama ayarlarını yönetme](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Ayar Kılavuzu

**Ayar Kılavuzu** uygulama ayarlarını yapılandırmak için kullanılır. Bu kılavuz, aşağıdaki sütunlar vardır:

**Ad**

Uygulama ayarı adı bu alana girin.

**Türü**

Ayar için bir tür seçmek için açılan listeyi kullanın. Aşağı açılan listeden, örneğin, en sık kullanılan türler görünür **dize**, **(bağlantı dizesi)**, ve **System.Drawing.Font**. Seçerek başka bir tür seçebilirsiniz **Gözat** listesi ve bir türden sonra seçerek sonunda **bir türü seçin** iletişim kutusu. Bir türü seçtikten sonra aşağı açılan listesinde (geçerli çözüm için yalnızca) ortak türlerine eklenir.

**Kapsam**

Şunlardan birini seçin **uygulama** veya **kullanıcı**.

Bağlantı dizeleri gibi uygulama kapsamlı ayarlar uygulamayla ilişkilendirilir. Kullanıcılar uygulama kapsamlı ayarlar çalışma zamanında değiştiremez.

Kullanıcı kapsamlı ayarları için kullanıcı tercihlerini kullanılacak yazı tipleri gibi amacını taşımaktadır. Kullanıcılar bunları çalışma zamanında değiştirebilir.

**Değer**

Veri veya uygulama ayarı ile ilişkili değer. Örneğin, bir yazı tipi ayarı ise değeri olabilir **9.75pt, stil Verdana Kalın =**.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme](../managing-application-settings-dotnet.md)
- [Erişim uygulama ayarları (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)