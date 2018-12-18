---
title: Dil sunucusu Protokolü'ne genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad0e802bd63a9d489a98eb9f216e6739e378d590
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894865"
---
# <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

## <a name="what-is-the-language-server-protocol"></a>Dil sunucusu protokolü nedir?

Kaynak kod otomatik tamamlama düzenleme özellikleri destekleyen zengin ister veya **Tanıma Git** geleneksel çok zor ve zaman alıcı bir düzenleyicide veya IDE bir programlama dili için. Genellikle bir etki alanı modeli (tarayıcı, bir ayrıştırıcı, bir tür denetleyicisi, bir oluşturucu ve daha fazla) düzenleyicimizi veya IDE'mizi programlama dilinde yazma gerektirir. Örneğin, Eclipse IDE Java dilinde yazılan beri C/c++ için Eclipse IDE desteği sağlar Eclipse CDT eklenti Java dilinde yazılır. Bu yaklaşımı Visual Studio Code için TypeScript, C/C++ etki alanı modeli ve ayrı etki alanı modeli içinde uygulama görünür duruma açardı C# Visual Studio için.

Dile özgü etki alanı modellerini oluşturma bir geliştirme aracı mevcut dile özgü kitaplıklar yeniden kullanabilir, çok daha kolay. Ancak, bu kitaplıklar, genellikle programlama dilinde kendi (modelleri C/C++'da uygulanır. Örneğin, iyi C/C++ etki alanı) uygulanır. C/C++ kitaplık içinde TypeScript yazılmış bir düzenleyicisine tümleştirme teknik olarak mümkün ama yapmak sabit değildir.

### <a name="language-servers"></a>Dil sunucuları

Başka bir kitaplık kendi işlem içinde çalıştırın ve işlemler arası iletişim için iletişim kurabilecek yaklaşımdır. Bir protokol İleri ve geri gönderilen iletileri oluşturur. Dil sunucusu Protokolü (LSP) bir geliştirme aracı ile dil sunucu işlemi arasında alınıp verilen iletileri Standartlaştırma ürünüdür. Dil sunucuları veya demons kullanarak yeni ya da yeni bir fikir değil. Vim ve Emacs anlam otomatik tamamlama desteği sağlamak bir süre bunu gibi düzenleyiciler. Bu tür tümleştirmeler basitleştirin ve çeşitli araçlar dil özellikleri açığa çıkarmak için kullanışlı bir çerçeve sunar LSP amacı oluştu.

Ortak bir protokolle dilin etki alanı modeli, mevcut bir uygulamasına yeniden kullanarak bir geliştirme aracı ile en az fuss içine dil özellikleri programlama tümleştirme sağlar. Bir dil server arka uç, PHP, Python veya Java yazılmış ve bu çeşitli araçları kolayca tümleştirilebilen LSP sağlar. Bir aracı için temel etki alanı modeli belirli farklılıklarına tam olarak anlamak gerek kalmadan zengin dil hizmetleri sağlayabilir, böylece protokolü, ortak bir soyutlama düzeyinde çalışır.

## <a name="how-work-on-the-lsp-started"></a>Nasıl kullanmaya LSP üzerinde çalışır

LSP zaman içinde gelişir ve bugün sürüm 3.0 olur. Dil sunucusu kavramını OmniSharp tarafından için zengin düzenleme özellikleri sağlamak üzere çekilmiş olduğunda başlatıldığından C#. Başlangıçta OmniSharp HTTP protokolü bir JSON yükü kullanılan ve birkaç düzenleyicileri dahil olmak üzere tümleşik [Visual Studio Code](https://code.visualstudio.com).

Aynı anda geçici olarak Microsoft Emacs ve Sublime Text gibi düzenleyicilerde TypeScript destekleme hakkında fikir ile bir TypeScript dil sunucu üzerinde çalışmaya başladı. Bu uygulamada, bir düzenleyici stdin/stdout TypeScript sunucu işlemi ile üzerinden iletişim kurar ve bir JSON yükü V8 hata ayıklayıcı protokolü tarafından ilham istekleri ve yanıtları için kullanır. TypeScript sunucunun TypeScript Sublime eklentisi ve VS Code TypeScript zengin düzenleme için tümleştirilmiştir.

İki farklı dil sunucu tümleşik sonra, bir ortak dil sunucusu protokolü düzenleyici ve IDE'ler için keşfetmek VS Code takım başlatıldı. Ortak bir protokolle farklı IDE'ler tarafından tüketilebilecek bir tek dil sunucu oluşturmak bir dil sağlayıcısı sağlar. Dil sunucusu tüketici yalnızca istemci tarafında protokolünün bir kez uygulamak vardır. Bu dil sağlayıcısı ve dil tüketici için win win durumda olur.

Dil sunucusu protokolü ile VS Code dil API'si tarafından ilham daha fazla dil özelliklerini genişleterek TypeScript sunucusu tarafından kullanılan protokol ile başlatıldı. Protokol basitliği ve mevcut kitaplıkları nedeniyle uzak çağrısı için JSON-RPC ile desteklenir.

VS team prototipli lint işlemi uygulanacak (tarama) yanıt birkaç lint dil sunucuları uygulayarak Protokolü istekleri bir dosyaya kod ve algılanan uyarılar ve hatalar bir dizi döndürür. Hedef lint işlemi uygulanacak bir düzenleyici oturumu sırasında birçok linting istekleri olacağını anlamına gelir. bir belgedeki kullanıcı düzenlemeleri olarak bir dosya oluştu. Bir sunucuyu ve yeni bir linting işlem her kullanıcı düzenleme için başlatılması gerekmeyen çalışıyor durumda tutmak için mantıklı bir seçimdi. VS Code'nın da dahil olmak üzere birçok lint sunucu uygulandığına Eslint'i ve Tslint'i uzantıları. Bu iki lint sunucu TypeScript/JavaScript uygulanan hem Node.js dosyasını çalıştırın. Bunlar, protokol, istemci ve sunucu parçası uygulayan bir kitaplık paylaşımı.

## <a name="how-the-lsp-works"></a>LSP nasıl çalışır?

Dil sunucusu kendi işleminde çalışır ve Visual Studio veya VS Code gibi araçlar dil protokolü kullanarak JSON-RPC üzerinden sunucusu ile iletişim. Dil sunucunun adanmış bir işlem olarak çalışan başka bir avantajı, tek bir işlem modeline ilgili performans sorunlarını kaçınılması sağlamasıdır. İstemci ve sunucu Node.js'de yazılmış gerçek taşıma kanalının stdio, yuva, adlandırılmış kanallar veya düğüm IPC ya da olabilir.

Aşağıdaki örnek nasıl bir yordam sırasında bir araç ve dil sunucusu iletişim kurmak için oturum düzenliyor:

![LSP Akış Diyagramı](media/lsp-flow-diagram.png)

* **Kullanıcı Aracı'nda (bir belge olarak adlandırılır) bir dosya açılır**: araç dil sunucunun bir belge açık olduğunu bildirir (' textDocument/didOpen'). Şu andan itibaren gerçekte belgesinin içeriğini hakkında artık dosya sisteminde değil ancak aracı bellekte tutulur.

* **Kullanıcının yaptığı düzenlemeler**: aracın sunucunun (' textDocument/didChange') Belge değişikliği hakkında size bildirir ve anlamsal bilgilerin programın dil sunucu tarafından güncelleştirilir. Böyle gibi dil server bu bilgileri analiz eder ve algılanan hataları ve Uyarıları (' textDocument/publishDiagnostics') aracıyla bildirir.

* **Kullanıcı "Tanıma Git" düzenleyicisindeki bir simgeye yürütür.**: aracı iki parametre ile bir ' textDocument/tanım' istek gönderir: (1) belge URI'si ve tanımı isteği Git sunucuya başlatıldığı gelen (2 metin konumu. Sunucu yanıt verir belge URI'si ve simgenin tanımını belgesinin içindeki konumu.

* **Kullanıcı ' % s'belgesi (dosya) kapatır**: belge artık bellek ve geçerli içeriğini şimdi artık dosya sisteminde güncel olan dil sunucusunun bildiren aracından ' textDocument/didClose' bildirim gönderilir.

Bu örnekte, protokol düzeyinde Düzenleyici Özellikleri "Tanıma", "Tüm başvuruları Bul" gibi dil sunucusuyla nasıl iletişim kurduğu gösterilmektedir. Protokolü tarafından kullanılan veri düzenleyicimizi veya IDE'mizi 'veri türleri' şu anda açık metin belgesi ve imleç konumu gibi türleridir. Veri türleri, genellikle soyut sözdizimi ağacı ve derleyici simgeleri (örneğin, çözümlenen türleri, ad,...) sağlayacak bir programlama dili etki alanı modeli düzeyinde değildir. Bu protokol önemli ölçüde basitleştirir.

Artık daha fazla ayrıntı ' textDocument/tanım' istekte göz atalım. İstemci aracında bir C++ belgede "Tanıma Git" istek için dil sunucusu arasında Git yüklerini aşağıdadır.

Bu istek.

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Bu yanıt.

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Geriye dönüp, düzenleyicinin düzeyinde yerine programlama dili model düzeyinde veri türlerini açıklayan dil sunucusu protokolü başarısını nedenlerle biridir. Bir metin belgesi URI standart hale getirmek çok basittir ya da bir imleç konumu bir soyut sözdizimi ağacını ve derleyici sembolleri farklı programlama dilleri arasında standart ile karşılaştırıldığında.

VS Code, genellikle bir kullanıcı farklı dilleriyle çalışırken, her programlama dili için bir dil sunucusu başlatır. Aşağıdaki örnek bir oturum kullanıcı Java ve SASS dosyalarını nerede çalıştığını gösterir.

![Java ve sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Özellikler

Her dil sunucusu protokolü tarafından tanımlanan tüm özelliklerini destekler. Bu nedenle, istemci ve sunucu, bunların 'özellikleri' desteklenen bir özellik kümesi sunar. Örneğin, ' textDocument/tanımı' isteği işleyebilir, ancak 'çalışma alanı/symbol' isteğini yerine değil bir sunucu olduğunu bildirir. Benzer şekilde, istemciler 'yaklaşık kaydetmek için ' sağlayabilir duyurmaktan, böylece bir sunucu otomatik olarak düzenlenen belge biçimlendirmek için metin düzenlemeleri hesaplayabilirsiniz belge kaydedilmeden önce bildirimleri.

## <a name="integrating-a-language-server"></a>Dil sunucusu tümleştirme

Belirli bir aracı bir dil sunucunun gerçek tümleştirme, dil sunucusu protokolü tarafından tanımlı değil ve aracı implementors için bırakılır. Bazı araçları başlatabilir ve konuşma dilini sunucusu herhangi bir türden bir uzantı sağlayarak dil sunucuları genel tümleştirin. Bir uzantı bazı özel dil özellikleri sağlamak hala böylece diğer dil sunucu başına özel uzantı VS Code gibi oluşturun.

Dil sunucular ve istemciler uygulamasını basitleştirmek için var. kitaplıkları veya SDK'ları için istemci ve sunucu bölümleri Bu kitaplıklar, farklı diller için sağlanır. Örneğin, bir [dil istemci npm modülünü](https://www.npmjs.com/package/vscode-languageclient) VS Code uzantısı ve başka bir dil sunucu tümleştirilmesi kolaylaştırmak için [dil sunucu npm modülünü](https://www.npmjs.com/package/vscode-languageserver) Node.js kullanarak bir dil sunucu yazma için. Bu, geçerli [listesi](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) destek kitaplıkları.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Dil sunucusu protokolü kullanarak Visual Studio'da

* [Dil sunucusu Protokolü uzantısı ekleme](adding-an-lsp-extension.md) -dil sunucu Visual Studio ile tümleştirme hakkında bilgi edinin.
