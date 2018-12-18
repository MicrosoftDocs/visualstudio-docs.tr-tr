---
title: Kod Parçacıkları İçin En İyi Uygulamalar
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8c7a04f2a2fb2ef59a41953c82da4254f213084
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179537"
---
# <a name="best-practices-for-using-code-snippets"></a>Kod parçacıkları için en iyi uygulamalar

Kod parçacığı kodda bir şey yalnızca en basit yol gösterir. Çoğu uygulama için kod uygulaması uyacak şekilde değiştirilmesi gerekir.

## <a name="handling-exceptions"></a>Özel durumları işleme

Genellikle, kod parçacığı deneyin... Catch blokları catch ve tüm özel durumları rethrow. Bu, projeniz için doğru seçim olmayabilir. Her özel durum için yanıt birkaç yolu vardır. Örnekler için bkz [nasıl yapılır: try/catch (C#) kullanarak bir özel durum işleme](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) ve [deneyin... Catch... Finally deyimi (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Dosya konumları

Dosya konumları uygulamanıza uyum, aşağıdakiler hakkında düşünün:

- Erişilebilir bir konumda bulunuyor. Kullanıcılar, erişimi olmayabilir *Program dosyaları* uygulamayla dosyaların depolanması Mayıs iş dosyaları değil, bu nedenle bilgisayarının klasör.

- Güvenli bir konumda bulunuyor. Dosya depolama kök klasöründe (*C:\\*) güvenli değildir. Uygulama verileri için öneririz *uygulama verileri* klasör. Bireysel kullanıcı verileri için uygulama her kullanıcı için bir dosya oluşturabilirsiniz *belgeleri* klasör.

- Geçerli bir dosya adı kullanıyor. Kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> geçersiz dosya adları olasılığını azaltmak için denetimleri. Bir dosya kullanıcının seçtiği zaman ve kodunuzu dosyasını yöneten zaman arasında dosya silinebilir dikkat edin. Ayrıca, kullanıcı dosyaya yazmak için gerekli izinlere sahip.

## <a name="security"></a>Güvenlik

Nasıl bir kod parçacığı güvenlidir, kaynak kodunda kullanıldığı ve kodda olduğunda nasıl değiştirilir bağlıdır. Aşağıdaki liste, dikkate alınması gereken alanların birkaçını içerir.

- Dosya ve veritabanı erişimi

- Kod erişimi güvenliği

- Kaynakları koruma (olay günlükleri, kayıt defteri)

- Gizli dizileri depolama

- Giriş doğrulanıyor

- Komut dosyası teknolojileri için veri geçirme

Daha fazla bilgi için [uygulamalarının güvenliğini sağlama](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>İndirilen kod parçacıkları

Visual Studio tarafından yüklenmiş IntelliSense kod parçacıkları kendisi içinde bir tehlike değildir. Ancak, bunlar uygulamanızda güvenlik risklerini oluşturabilirsiniz. Internet'ten indirilen kod parçacıkları gibi diğer tüm indirilen içeriği - işlemini çok dikkatli olunmalıdır.

- Yalnızca güvendiğiniz sitelerden parçacıkları indirir ve güncel virüsten yazılımı kullanın.

- Tüm indirilen kod parçacığı dosyaları Not Defteri veya Visual Studio XML düzenleyicisinde açın ve yüklemeden önce dikkatle gözden geçirin. Aşağıdaki sorunları arayın:

    - Bunu, kod parçacığı sisteminize zarar verebilir. Kaynak kodu çalıştırmadan önce dikkatle okuyun.

    - Kod parçacığı dosyasını Yardım URL'si bloğunu bir kötü amaçlı bir komut dosyası yürütme veya rahatsız edici bir Web sitesi görüntüleme URL'leri içerebilir.

    - Kod parçacığı sessizce projenize eklenir ve herhangi bir yere sisteminize yüklenebilir başvuruları içerebilir. Bu başvurular bilgisayarınıza kod parçacığını indirdiğiniz gelen indirilmiş olabilir. Kod parçacığı, ardından kötü amaçlı kod yürüten başvurusunda bir yönteme bir çağrı yapabilir. Tür bir saldırıya karşı korunmak için kod parçacığı dosyasını içeri aktarmalar ve başvurular bloklarını gözden geçirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense kod parçacıkları](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Uygulamalarının güvenliğini sağlama](../ide/securing-applications.md)
- [Kod parçacıkları](../ide/code-snippets.md)