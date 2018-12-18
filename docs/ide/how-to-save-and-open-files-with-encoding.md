---
title: 'Nasıl yapılır: kaydedin ve açık dosyaları kodlamayla'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6298e603589d41a6a082b6fe2c1916b3cf8a2a84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943065"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Nasıl yapılır: kaydedin ve açık dosyaları kodlamayla

Özel karakter çift yönlü dilleri desteklemek için kodlama dosyalarını kaydedebilirsiniz. Ayrıca, böylece Visual Studio dosyanın doğru görüntüler bir bir dosyayı açarken kodlama belirtebilirsiniz.

## <a name="to-save-a-file-with-encoding"></a>Dosya kodlama ile kaydetmek için

1.  Gelen **dosya** menüsünde seçin **dosyasını Farklı Kaydet**, tıklattıktan sonra açılan düğmesine yanına **kaydetmek** düğmesi.

     **Gelişmiş kaydetme seçenekleri** iletişim kutusu görüntülenir.

2.  Altında **kodlama**, dosya için kullanılacak kodlama seçin.

3.  İsteğe bağlı olarak, altında **satır sonları**, satır sonu karakterleri biçimini seçin.

     Bu seçenek, dosyayı farklı bir işletim sistemi kullanıcılarla exchange istiyorsanız yararlıdır.

     Özel bir biçimde kodlanmış bildiğiniz bir dosyayla çalışmak isterseniz, bu dosyayı açarken kodlama kullanmak için Visual Studio anlayabilirsiniz. Kullandığınız yöntem dosyayı projenize bir parçası olmasına bağlıdır.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Bir projesinin bir parçası olan bir kodlanmış dosyayı açmak için

1.  İçinde **Çözüm Gezgini**, dosyaya sağ tıklayın ve seçin **birlikte Aç**.

2.  İçinde **birlikte Aç** iletişim kutusunda, dosyayı açmaya Düzenleyicisi'ni seçin.

     Forms düzenleyici gibi birçok Visual Studio düzenleyicileri kodlama Otomatik Algıla ve dosyanın uygun şekilde açın. Bir kodlama seçmenize olanak tanıyan bir Düzenleyicisi'ni seçerseniz **kodlama** iletişim kutusu görüntülenir.

3.  İçinde **kodlama** iletişim kutusunda, düzenleyicinin kullanması gereken kodlama seçin.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Bir proje parçası olmayan bir kodlanmış dosyayı açmak için

1.  Üzerinde **dosya** menüsündeki **açmak**, seçin **dosya** veya **Web'den dosya**ve ardından açmak için dosyayı seçin.

2.  Açılan düğmesine tıklayın **açık** düğmesini tıklatın ve seçin **birlikte Aç**.

3.  Adım 2 ve 3 yukarıdaki yordamı izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlama ve satır sonları](encodings-and-line-breaks.md)
- [Kodlama ve Windows Forms Genelleştirme](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalize ve uygulamaları yerelleştirme](../ide/globalizing-and-localizing-applications.md)