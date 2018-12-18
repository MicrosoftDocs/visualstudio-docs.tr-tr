---
title: Uygulama ayarlarını yönetme (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4ea61199159e68f3707b6dac4d3a6c1f5ea7635
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671793"
---
# <a name="manage-application-settings-net"></a>Uygulama ayarlarını yönetme (.NET)

Uygulama ayarları, uygulama bilgilerini dinamik olarak depolamanıza olanak sağlar. Ayarları, uygulama kodu (örneğin bir bağlantı dizesi), kullanıcı tercihlerine ve çalışma zamanında gereken diğer bilgilere dahil edilmemesi gereken istemci bilgisayarda bilgileri depolamak sağlar.

Uygulama ayarları, Visual Studio'nun önceki sürümlerinde kullanılan dinamik özellikleri değiştirir.

Her uygulama ayarının benzersiz bir ad olmalıdır. Ad harf, sayı veya bir rakamla başlamaz bir alt çizgi herhangi bir birleşimi olabilir ve boşluk olamaz. Adı aracılığıyla değiştirilir `Name` özelliği.

Uygulama ayarları, XML'e seri veya veri türü olarak depolanabilir bir `TypeConverter` uygulayan `ToString` / `FromString`. En yaygın türler `String`, `Integer`, ve `Boolean`, ancak değerleri olarak da depolayabilirsiniz <xref:System.Drawing.Color>, <xref:System.Object>, veya bir bağlantı dizesi.

Uygulama ayarları, ayrıca bir değer tutar. İle değerin ayarlanması **değer** özelliği ve ayarın veri türüyle eşleşmelidir.

Ayrıca, uygulama ayarları, tasarım zamanında bir form veya denetim özelliğine bağlanabilir.

Uygulama ayarları kapsamına göre iki tür vardır:

- Uygulama kapsamlı ayarlar, bir web hizmeti veya veritabanı bağlantı dizesi için URL gibi bilgilere için kullanılabilir. Bu değerler uygulamayla ilişkilendirilir. Bu nedenle, kullanıcılar bunları çalışma zamanında değiştiremez.

- Kullanıcı kapsamlı ayarları, son konum bir form veya bir yazı tipi tercihini kalıcı yapma gibi bilgileri için kullanılabilir. Kullanıcılar, çalışma zamanında bu değerleri değiştirebilir.

Bir ayarın türünü kullanarak değiştirebileceğiniz **kapsam** özelliği.

Proje sistemi uygulama ayarlarını iki XML dosyasında depolar:

- bir *app.config* ilk uygulama ayarını oluşturduğunuzda tasarım zamanında oluşturulan dosya

- bir *user.config* uygulamayı çalıştıran kullanıcının, herhangi bir kullanıcı ayarı değerini değiştiğinde çalışma zamanında oluşturulan dosya.

Kullanıcı ayarlarındaki değişikliklerin, uygulama özellikle Bunu yapmak için bir yöntem çağırmadığı sürece diske yazılmadığına dikkat edin.

## <a name="create-application-settings-at-design-time"></a>Tasarım zamanında uygulama ayarları oluşturma

Tasarım zamanında uygulama ayarları iki şekilde oluşturabilirsiniz: kullanarak **ayarları** sayfasının **Proje Tasarımcısı**, kullanarak veya **özellikleri** penceresi için bir form veya Denetim ayarı bir özelliğe bağlayabileceğiniz olanak tanır.

Bir uygulama kapsamlı ayar (örneğin, bir veritabanı bağlantı dizesi, veya sunucu kaynaklarına bir başvuru) oluşturduğunuzda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] içinde kaydeder *app.config* ile `<applicationSettings>` etiketi. (Bağlantı dizeleri altına kaydedilir `<connectionStrings>` etiketi.)

Kullanıcı kapsamlı (örneğin, varsayılan yazı tipi, giriş sayfası veya pencere boyutu), bir ayar oluşturduğunuzda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] içinde kaydeder *app.config* ile `<userSettings>` etiketi.

> [!IMPORTANT]
> Bağlantı dizelerini depoladığınız zaman *app.config*, parolalar veya bağlantı dizesinde sunucu yolları gibi hassas bilgileri açıklanmaması için önlem almalısınız.
>
> Bağlantı dizesi bilgilerini bir dış kaynaktan izlerseniz, bir kullanıcı kimliği ve parolası, dikkatli olmalıdır sağlayan bir kullanıcı gibi bağlantınızı oluşturmak için kullandığınız değerleri emin olmak için dize içermiyor ek bağlantı dizesi parametreleri bağlantınızı davranışını değiştirebilirsiniz.
>
> Yapılandırma dosyasındaki hassas bilgileri şifrelemek için korumalı yapılandırma özelliğini kullanmayı düşünün. Daha fazla bilgi için [bağlantı bilgilerini korumak](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Sınıf kitaplıkları için bir yapılandırma dosyası modeli olmadığından, uygulama ayarları sınıf kitaplığı projeleri için geçerli değildir. Bir yapılandırma dosyası olabilen DLL Office projesi için Visual Studio Araçları istisnadır.

## <a name="use-customized-settings-files"></a>Özelleştirilmiş ayar dosyalarını kullanma

Ayar gruplarının kolay yönetimi için projenize özelleştirilmiş ayar dosyaları ekleyebilirsiniz. Tek bir dosyada bulunan ayarlar yüklenir ve bir birim olarak kaydedilir. Ayrı dosyalarda ayarlarını depolama, sık kullanılan ve kullanılmayan gruplar zaman yükleme ve ayarları kaydediliyor kaydedebilirsiniz.

Örneğin, bir dosya gibi ekleyebilirsiniz *SpecialSettings.settings* projenize. Ancak, `SpecialSettings` sınıfı gösterilmese de `My` ad alanı, **kodu görüntüle** içeren özel ayarlar dosyasını okuyabilir `Partial Class SpecialSettings`.

**Ayarlar Tasarımcısı** ilk arar *Settings.settings* dosya proje sisteminin oluşturduğu; bu dosya varsayılan dosya **Proje Tasarımcısı** görüntüler **ayarları** sekmesi. *Settings.Settings* bulunan *Projem* klasör [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeleri ve *özellikleri* klasör [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeleri. **Proje Tasarımcısı** projenin kök klasöründeki diğer ayarlar dosyalarını arar. Bu nedenle, özel ayarlar dosyanızı buraya koymanız gerekir. Eklerseniz bir *.settings* projenize, başka bir yerde dosyasında **Proje Tasarımcısı** bulmak mümkün olmayacaktır.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Visual Basic'te çalışma zamanında uygulama ayarları erişim veya değiştirme

Visual Basic projelerinde, uygulama ayarları çalışma zamanında kullanarak erişebileceğiniz `My.Settings` nesne. Üzerinde **ayarları** sayfasında **kod** görüntülemek için düğmeyi *Settings.vb* dosya. *Settings.vb* tanımlar `Settings` ayarlar sınıfındaki bu olayları işlemenizi sağlar sınıfını: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Dikkat `Settings` sınıfını *Settings.vb* görüntüler yalnızca kullanıcıya ait kodu, tüm oluşturulan sınıfı değil kısmi bir sınıftır. Kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi için `My.Settings` nesne, bkz: [erişim uygulama ayarları (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Kullanıcı değişiklikleri (örneğin, formun konumu) çalışma zamanında depolanan kullanıcı kapsamlı ayarların değerleri bir *user.config* dosya. Varsayılan değerlerin hala kaydedilen bildirimi *app.config*.

Kullanıcı kapsamlı ayarları uygulamayı test etme, örneğin, çalışma zamanında değiştirilmiş ve bu ayarları varsayılan değerlerine sıfırlamak istiyorsanız **Eşitle** düğmesi.

Kullanmanızı öneririz `My.Settings` nesne ve varsayılan *.settings* ayarlara erişmek için dosya. Kullanabileceğiniz olmasıdır **ayarlar Tasarımcısı** ayarları ve kullanıcı için Ayrıca, özellikler atamak için ayarlar uygulama kapatma önce otomatik olarak kaydedilir. Ancak, Visual Basic uygulamasında ayarlarına doğrudan erişebilirsiniz. Bu durumda, zorunda erişim `MySettings` sınıfı ve özel bir kullanın *.settings* projenin köküne dosya. Bir C# uygulaması için yaptığınız gibi uygulamayı sonlandırmadan önce kullanıcı ayarlarını kaydetmeniz gerekir; Bu, aşağıdaki bölümde açıklanmıştır.

## <a name="access-or-change-application-settings-at-run-time-in-c"></a>C# ' de çalışma zamanında erişim ya da değişiklik uygulama ayarları #

Visual Basic, C# gibi dışındaki dillerde, erişmelisiniz `Settings` doğrudan, aşağıda gösterildiği gibi sınıf [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] örnek.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Açıkça çağırmalıdır `Save` kullanıcı ayarlarını korumak için bu sarmalayıcı sınıfının yöntemi. Genellikle bunu `Closing` olay işleyicisi ana formu. Aşağıdaki C# örneği için bir çağrı gösterir `Save` yöntemi.

```csharp
Properties.Settings.Default.Save();
```

Üzerinden uygulama ayarlarına erişme hakkında genel bilgi `Settings` sınıfı [uygulama ayarlarına genel bakış (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Ayarlar üzerinden yineleme hakkında daha fazla bilgi için bkz. Bu [forum gönderisi](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Ayrıca bkz.

- [Erişim uygulama ayarları (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
