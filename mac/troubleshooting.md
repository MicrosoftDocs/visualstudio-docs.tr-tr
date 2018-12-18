---
title: Sorun giderme
description: Genel sorunlar ve çözümleri Visual Studio için Mac kullanıcıları için.
ms.topic: troubleshooting
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 3a5ea59e6f98891cd113ccad9a74038ca52cccf8
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294649"
---
# <a name="troubleshooting"></a>Sorun giderme

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Mac için Visual Studio'da günlüklerini görüntüleme

Günlükleri göz atarak bulunabilir **Yardım > açık günlük dizini** menü öğesi, aşağıda gösterildiği gibi:

![Günlük dizini menü öğesini Aç](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Özel durumları görüntüleme

Bir özel durum yakalandığında, bir özel durum Kabarcık görünür. Daha fazla ayrıntı görüntülemek için seçin **ayrıntıları** düğmesi:

![Bir özel durum hakkında daha fazla ayrıntı görüntüleyin](media/troubleshooting-image2.png)

Bu görüntüler **ayrıntıları göster** özel durumla ilgili daha fazla bilgi verdiğiniz iletişim kutusunda:

![Ayrıntıları iletişim kutusunu göster](media/troubleshooting-image3.png)

Yukarıda numaralı iletişim önemli bölümleri aşağıda ayrıntılı olarak açıklanmıştır:

1. Özel durum türünün tam adını gösteren özel durum türü dikkate alınır.
2. Özel durum iletisi ileti özelliği, özel durum nesnesi değerini gösterir.
3. Özel durum türünün tam adını şu anda seçili özel durum için iç özel durum ağaç görünümünde gösterir. iç özel durum türü.
4. İç özel durum iletisi, iç özel durum ağaç görünümünde seçilen özel durumun iletisi özelliğinin değeri gösterir.
5. Stacktrace görüntüleyin. Bu, bir açıklama ok daraltılmış ve yığın çerçeveleri girişler içeriyor.
6. Kullanıcı olmayan kod girişleri örneği.
7. Örnek kullanıcı kodu girdi.
8. Özellikler Görünümü tüm özellikleri ve özel alanları gösterir. Bu, bir açıklama ok daraltılabilirler.
9. İç özel duruma ağaç görünümü. Yukarı/aşağı okları veya fare ya da izleme paneli ile klavyeden bu görünümde iç özel durumlar'ı seçin.
10. Varsayılan olarak, bu ne ayarlanır **yalnızca proje kodunda hata ayıklama** hata ayıklayıcı ayarlarında seçeneği ayarlanır. Bu kutuyu seçerek, tek bir satır olarak stacktrace daraltmak tüm kullanıcı olmayan kod olanak sağlar.
11. Kopyalamak için Kopyala düğmesine `exception.ToString()` panoya çıktı.

Özel bir iç özel duruma sahip olduğunda bu bölümlerin bazıları yalnızca görünür olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [(Windows için Visual Studio) IDE hatalarında sorun giderme kaynakları](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)