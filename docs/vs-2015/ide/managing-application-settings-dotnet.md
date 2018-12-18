---
title: Uygulama ayarları (.NET) yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac4f670b813970d027925b681a2e3211e1898e1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866135"
---
# <a name="managing-application-settings-net"></a>Uygulama Ayarlarını Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama ayarları, uygulama bilgilerini dinamik olarak depolamanıza olanak sağlar. Ayarları, uygulama kodu (örneğin bir bağlantı dizesi), kullanıcı tercihlerine ve çalışma zamanında gereken diğer bilgilere dahil edilmemesi gereken istemci bilgisayarda bilgileri depolamak sağlar.  
  
 Uygulama ayarları, Visual Studio'nun önceki sürümlerinde kullanılan dinamik özellikleri değiştirir.  
  
 Her uygulama ayarının benzersiz bir ad olmalıdır. Ad harf, sayı veya bir rakamla başlamaz bir alt çizgi herhangi bir birleşimi olabilir ve boşluk içeremez. Adı aracılığıyla değiştirilebilir `Name` özelliği.  
  
 Uygulama ayarları, XML'e seri hale getirilebilir veya veri türü olarak depolanabilir bir `TypeConverter` uygulayan `ToString` / `FromString`. En yaygın türler `String`, `Integer`, ve `Boolean`, ancak değerleri olarak da depolayabilirsiniz <xref:System.Drawing.Color>, <xref:System.Object>, veya bir bağlantı dizesi.  
  
 Uygulama ayarları, bir değer de içerir. İle değerin ayarlanması **değer** özelliği ve ayarın veri türüyle eşleşmelidir.  
  
 Ayrıca, uygulama ayarları, tasarım zamanında bir form veya denetim özelliğine bağlanabilir.  
  
 Uygulama ayarları kapsamına göre iki tür vardır:  
  
- Uygulama kapsamlı ayarlar, bir Web hizmeti veya veritabanı bağlantı dizesi için URL gibi bilgilere için kullanılabilir. Bu değerler uygulamayla ilişkilendirilir. Bu nedenle, kullanıcılar bunları çalışma zamanında değiştiremez.  
  
- Kullanıcı kapsamlı ayarları, son konum bir form veya bir yazı tipi tercihini kalıcı yapma gibi bilgileri için kullanılabilir. Kullanıcılar, çalışma zamanında bu değerleri değiştirebilir.  
  
  Bir ayarın türünü kullanarak değiştirebileceğiniz **kapsam** özelliği.  
  
  Proje sistemi uygulama ayarlarını iki XML dosyasında depolar: ilk uygulama ayarını oluşturduğunuzda tasarım zamanında oluşturulan bir app.config dosyası ve uygulamayı çalıştıran kullanıcının herhangi bir kullanıcı ayarı değerini değiştiğinde çalışma zamanında oluşturulan bir user.config dosyası. Kullanıcı ayarlarındaki değişikliklerin, uygulama özellikle Bunu yapmak için bir yöntem çağırmadığı sürece diske yazılmadığına dikkat edin.  
  
## <a name="creating-application-settings-at-design-time"></a>Tasarım zamanında uygulama ayarları oluşturma  
 Tasarım zamanında uygulama ayarları iki şekilde oluşturabilirsiniz: kullanarak **ayarları** sayfasının **Proje Tasarımcısı**, kullanarak veya **özellikleri** penceresi için bir form veya Denetim ayarı bir özelliğe bağlayabileceğiniz olanak tanır.  
  
 Bir uygulama kapsamlı ayar (örneğin, bir veritabanı bağlantı dizesi, veya sunucu kaynaklarına bir başvuru) oluşturduğunuzda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] App.config'e kaydeder `<applicationSettings>` etiketi. (Bağlantı dizeleri altına kaydedilir `<connectionStrings>` etiketi.)  
  
 Kullanıcı kapsamlı (örneğin, varsayılan yazı tipi, giriş sayfası veya pencere boyutu), bir ayar oluşturduğunuzda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] App.config'e kaydeder `<userSettings>` etiketi.  
  
> [!IMPORTANT]
>  Bağlantı dizelerini app.config dosyasında depoladığınızda, parolalar veya bağlantı dizesinde sunucu yolları gibi hassas bilgileri açıklanmaması için önlemleri almalıdır.  
>   
>  Bağlantı dizesi bilgilerini bir dış kaynaktan izlerseniz, bir kullanıcı kimliği ve parolası, dikkatli olmalıdır sağlayan bir kullanıcı gibi bağlantınızı oluşturmak için kullandığınız değerleri emin olmak için dize içermiyor ek bağlantı dizesi parametreleri bağlantınızı davranışını değiştirebilirsiniz.  
>   
>  Yapılandırma dosyasındaki hassas bilgileri şifrelemek için korumalı yapılandırma özelliğini kullanmayı düşünün. Bkz: [bağlantı bilgilerini koruma](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4) daha fazla bilgi için.  
  
> [!NOTE]
>  Sınıf kitaplıkları için bir yapılandırma dosyası modeli olmadığından, uygulama ayarları sınıf kitaplığı projeleri için geçerli değildir. Bir yapılandırma dosyası olabilen DLL Office projesi için Visual Studio Araçları istisnadır.  
  
## <a name="using-customized-settings-files"></a>Özelleştirilmiş ayar dosyalarını kullanma  
 Ayar gruplarının kolay yönetimi için projenize özelleştirilmiş ayar dosyaları ekleyebilirsiniz. Tek bir dosyada bulunan ayarlar yüklenir ve bir birim olarak kaydedilir. Bu nedenle, ayarları için ayrı dosyalara depolamak için sık kullanılan ve kullanılmayan gruplar, yükleme ve ayarları kaydediliyor zamandan tasarruf edebilirsiniz.  
  
 Örneğin, SpecialSettings.settings gibi bir dosyayı projenize ekleyebilirsiniz. Ancak, `SpecialSettings` sınıfı gösterilmese de `My` ad alanı, **kodu görüntüle** içeren özel ayarlar dosyasını okuyabilir `Partial Class SpecialSettings`.  
  
 Ayarlar Tasarımcısı önce proje sisteminin oluşturduğu Settings.settings dosyasını arar; Bu, Proje Tasarımcısı görüntüler varsayılan dosyadır **ayarları** sekmesi. Settings.Settings için Projelerim klasöründe bulunan [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeleri için özellikler klasöründe ve [!INCLUDE[csprcs](../includes/csprcs-md.md)] projeleri. Proje Tasarımcısı sonra projenin kök klasöründeki diğer ayarlar dosyalarını arar. Bu nedenle, özel ayarlar dosyanızı buraya koymanız gerekir. Bir .settings dosyası projenize başka bir yerde eklerseniz, Proje Tasarımcısı bunu bulamaz olmayacaktır.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Uygulama ayarlarına erişme veya Visual Basic'te çalışma zamanında uygulama ayarlarını değiştirme  
 İçinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeleri kullanarak çalışma zamanında uygulama ayarlarına erişebilirsiniz `My.Settings` nesne. Üzerinde **ayarları** sayfasında **kod** Settings.vb dosyasını görüntülemek için düğme. Settings.vb tanımlar `Settings` ayarlar sınıfındaki bu olayları işlemenizi sağlar sınıfını: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Dikkat `Settings` Settings.vb sınıfı, yalnızca kullanıcıya ait kodu tüm oluşturulan sınıfı değil görüntüleyen bir parçalı sınıf. Kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi için `My.Settings` nesne, bkz: [uygulama ayarlarına erişme](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).  
  
 (Örneğin, formun konumu) çalışma zamanında kullanıcı değiştirdiği kullanıcı kapsamlı ayarların değerleri user.config dosyasında depolanır. Varsayılan değerlerin hala app.config dosyasında kaydedildiğine dikkat edin.  
  
 Uygulamayı test etme, örneğin, çalışma zamanında kullanıcı kapsamlı ayarları değişti ve istiyorsanız bu ayarları varsayılan değerlerine sıfırlamak **Eşitle** düğmesi.  
  
 Kullanmanızı öneririz `My.Settings` nesne ve varsayılan .settings dosyasını erişim ayarları. Ayarlara özellikler atamak için ayarlar Tasarımcısı'nı kullanabilirsiniz ve ayrıca, kullanıcı ayarları otomatik olarak uygulama kaydedilmesidir nedeni budur. Ancak, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] uygulama ayarlara doğrudan erişebilir. Bu durumda sahip olduğunuz erişim `MySettings` sınıfı ve bir proje kökündeki özel .settings dosyasını kullanın. Bir C# uygulaması için yaptığınız gibi uygulamayı sonlandırmadan önce kullanıcı ayarlarını da kaydetmelisiniz; Bu, aşağıdaki bölümde açıklanmıştır.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Uygulama ayarlarına erişme veya Visual C# ' de çalışma zamanında uygulama ayarlarını değiştirme  
 Dışındaki dillerde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], gibi [!INCLUDE[csprcs](../includes/csprcs-md.md)], erişmesi gereken `Settings` doğrudan, aşağıda gösterildiği gibi sınıf [!INCLUDE[csprcs](../includes/csprcs-md.md)] örnek.  
  
```csharp  
Properties.Settings.Default.FirstUserSetting = "abc";  
```  
  
 Aynı zamanda açıkça çağırmalıdır `Save` kullanıcı ayarlarını korumak için bu sarmalayıcı sınıfının yöntemi. Genellikle bunu `Closing` olay işleyicisi ana formu. Aşağıdaki [!INCLUDE[csprcs](../includes/csprcs-md.md)] örnek çağırmayı gösterir `Save` yöntemi.  
  
```csharp  
Properties.Settings.Default.Save();  
```  
  
 Üzerinden uygulama ayarlarına erişme hakkında genel bilgi `Settings` sınıfı [uygulama ayarlarına genel bakış](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Ayarlar üzerinden yineleme hakkında daha fazla bilgi için bkz. Bu [forum gönderisi](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Ayarlarına Erişme](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)



