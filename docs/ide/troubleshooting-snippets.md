---
title: Kod parçacıkları sorunlarını giderme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61485e50c61580b69c1dfcb5434849ea9122bde7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942341"
---
# <a name="troubleshoot-snippets"></a>Kod parçacıkları sorunlarını giderme

IntelliSense kod parçacıkları ile ilgili sorunlar genellikle iki sorunları neden: hatalı kod parçacığı dosyasının içeriğini ya da bozuk kod parçacığı dosyası.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Kod parçacığı bir Visual Studio kaynak dosyası için dosya Gezgini'nden sürüklenemez

- XML kod parçacığı dosyası bozulmuş olabilir. **XML Düzenleyicisi** içinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sorunları XML yapısı içinde bulabilirsiniz.

- Kod parçacığı dosyasını kod parçacığı şemaya uygun olmayabilir. **XML Düzenleyicisi** içinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sorunları XML yapısı içinde bulabilirsiniz.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kodu değil vurgulanan derleyici hataları var

-   Bir proje başvurusu eksik olabilir. Kod parçacığı hakkında belgeleri inceleyin. Referans bilgisayarda bulunmazsa yüklemeniz gerekir. Bir kod parçacığı eklemeden, gerekli tüm başvuruları projeye eklemeniz gerekir. Kod parçacığı başvuru bilgileri eksikse, hata olarak için kod parçacığı Oluşturucu bildirilebilir.

-   Bir değişken tanımlanmamış olabilir. Tanımlanmamış bir kod parçacığı değişkenlerinde vurgulanmış olmalıdır. Aksi durumda, kod parçacığı oluşturan hata olarak bildirilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
