---
title: Hizmetler Sayfası, Proje Tasarımcısı
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba03b4aea25decef39983d203db12dfbedc516d9
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177025"
---
# <a name="services-page-project-designer"></a>Hizmetler Sayfası, Proje Tasarımcısı

İstemci uygulama hizmetleri için Basitleştirilmiş erişim sağlayan [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] oturum açma, roller ve profil hizmetlerinden Windows Forms ve Windows Presentation Foundation (WPF) uygulamaları. Kullanabileceğiniz **Hizmetleri** sayfasının **Proje Tasarımcısı** etkinleştirme ve istemci uygulama hizmetleri, projeniz için yapılandırma.

İstemci uygulama hizmetleri ile kullanıcıların kimliğini doğrulama, her kullanıcının atanan rolü veya rolleri belirlemek ve ağ üzerinden paylaşabilirsiniz kullanıcı başına uygulama ayarlarını depolamak için merkezi bir sunucu kullanabilirsiniz. Daha fazla bilgi için [istemci uygulama hizmetleri](/dotnet/framework/common-client-technologies/client-application-services).

Erişim için **Hizmetleri** sayfasında, içinde bir proje düğümü seçin **Çözüm Gezgini**ve ardından **özellikleri** üzerinde **proje** menüsü. Zaman **Proje Tasarımcısı** görünen tıklayın **Hizmetleri** sekmesi.

## <a name="task-list"></a>Görev Listesi

[Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Yapılandırma**

 Bu sayfada bu denetim düzenlenemez. Bu denetimin açıklaması için bkz [derleme sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [derleme sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platform**

 Bu sayfada bu denetim düzenlenemez. Bu denetimin açıklaması için bkz [derleme sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [derleme sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **İstemci uygulama hizmetlerini etkinleştirmek**

 İstemci uygulama hizmetlerini etkinleştirmek için bu seçeneği seçin. Servis yerlerini belirtmeniz gerekir **Hizmetleri** sayfasına istemci uygulama hizmetleri kullanın.

 **Windows kimlik doğrulaması kullan**

 Kimlik doğrulama sağlayıcısı Windows tabanlı kimlik doğrulaması, diğer bir deyişle, Windows işletim sistemi tarafından sağlanan kimlik kullanacağını gösterir.

 **Forms kimlik doğrulaması kullan**

 Kimlik doğrulama sağlayıcısı form kimlik doğrulaması kullandığını gösterir. Başka bir deyişle, uygulamanız için oturum açma kullanıcı arabirimi sağlamanız gerekir. Daha fazla bilgi için [nasıl yapılır: istemci uygulama hizmetleri ile kullanıcı oturumu uygulama](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Kimlik doğrulama hizmet konumu**

 Yalnızca form kimlik doğrulaması ile kullanılır. Kimlik doğrulama hizmetinin konumunu belirtir.

 **İsteğe bağlı: Kimlik bilgileri sağlayıcısı**

 Yalnızca form kimlik doğrulaması ile kullanılır. Gösterir <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> uygulamanız çağırdığında bir oturum açma iletişim kutusunu görüntülemek için kimlik doğrulama hizmetinin kullanacağı uygulama `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> yöntemi ve geçişleri boş dizeler veya `null` parametre. Bu kutuyu boş bırakırsanız, geçerli kullanıcı adı ve parola geçmelidir <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> yöntemi. Kimlik bilgileri sağlayıcısı bir derleme nitelikli tür adı olarak belirtmeniz gerekir. Daha fazla bilgi için <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> ve [derleme adları](/dotnet/framework/app-domains/assembly-names). En basit şekliyle, bir derleme nitelikli tür adı, aşağıdaki örneğe benzer: `MyNamespace.MyLoginClass, MyAssembly`

 **Rol hizmet konumu**

 Rol hizmetinin konumunu belirtir.

 **Web ayarları hizmet konumu**

 Profil (web ayarları) hizmetinin konumunu belirtir.

 **Gelişmiş**

 Açılır [Hizmetleri iletişim kutusu için Gelişmiş ayarları](../../ide/reference/advanced-settings-for-services-dialog-box.md), bu varsayılan davranışı geçersiz kılmak için kullanabilirsiniz. Örneğin, bir veritabanı yerine yerel dosya sistemi kullanılarak çevrimdışı depolama belirtmek için bu iletişim kutusunu kullanabilirsiniz. Daha fazla bilgi için [Hizmetleri iletişim kutusu için Gelişmiş ayarları](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Uygulama Servisleri](/dotnet/framework/common-client-technologies/client-application-services)
- [Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)
