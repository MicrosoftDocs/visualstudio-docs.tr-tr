---
title: 'CA3147: ValidateAntiForgeryToken ile fiil işleyicilerini işaretleme'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: da15a441a10f3ad3f3f84ee0cc76eeed8e4127e4
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42624399"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: ValidateAntiForgeryToken ile fiil işleyicilerini işaretleme

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Bir ASP.NET MVC denetleyici eylem yöntemi ile işaretlenmemiş [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)), ya da HTTP fiili gibi belirten bir özniteliği [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993(v%3dvs.118)) veya [ AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Kural açıklaması

ASP.NET MVC denetleyicisi tasarlarken siteler arası istek sahteciliği saldırılarına oluşturduğunu unutmayın. Siteler arası istek Sahtekarlığı Saldırısı, kimliği doğrulanmış bir kullanıcıdan, ASP.NET MVC denetleyicisine kötü amaçlı istek gönderebilirsiniz. Daha fazla bilgi için [ASP.NET MVC ve web sayfalarında XSRF/CSRF önleme](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Bu kural denetler, ASP.NET MVC denetleyici eylem yöntemleri ya da:

- Sahip [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108%28v%3dvs.118%29) ve HTTP GET içermeden, izin verilen HTTP fiilleri belirtin.

- HTTP GET, izin verilen bir fiili belirtin.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

- HTTP GET isteklerini işleyen ve potansiyel olarak zararlı yan etkileri yoksa ASP.NET MVC denetleyici eylemleri için ekleme bir [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993%28v%3dvs.118%29) yöntemi.

   Bir ASP.NET MVC HTTP GET'ini işler denetleyici eylemi ister ve hassas verileri değiştirme gibi zararlı yan etkileri varsa, uygulamanızı siteler arası istek sahteciliği saldırılarına karşı savunmasız.  Hassas işlemleri yalnızca HTTP POST, PUT ve DELETE isteklerini gerçekleştirmek için uygulamanızı yeniden tasarlamanız gerekir.

- HTTP POST işleyen, ASP.NET MVC denetleyici eylemleri için PUT veya DELETE istekleri, ekleme [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)) ve izin verilen HTTP fiilleri belirten öznitelikler ([AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29) [HttpPostAttribute](/previous-versions/aspnet/web-frameworks/ee264023%28v%3dvs.118%29), [HttpPutAttribute](/previous-versions/aspnet/web-frameworks/ee470909%28v%3dvs.118%29), veya [HttpDeleteAttribute](/previous-versions/aspnet/web-frameworks/ee470917%28v%3dvs.118%29)). Ayrıca, çağırmanız gerekir [HtmlHelper.AntiForgeryToken()](/previous-versions/aspnet/web-frameworks/dd504812%28v%3dvs.118%29) MVC görünümü veya Razor web sayfası yöntemi. Bir örnek için bkz. [düzenleme metotlarını inceleme ve düzenleme görünümü](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu, bu kuraldan bir uyarıyı bastırmak güvenli değil:

- ASP.NET MVC denetleyicisi eylemi zararlı yan etkileri vardır.

- Uygulamayı farklı bir yolla antiforgery belirteci doğrular.

## <a name="validateantiforgerytoken-attribute-example"></a>ValidateAntiForgeryToken öznitelik örneği

### <a name="violation"></a>İhlali

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>HttpGet öznitelik örneği

### <a name="violation"></a>İhlali

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
