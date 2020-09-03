---
title: DSL tanımlarına uzantılar ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fab56a7738ed7b52760cf20a5bfcc8542ee5a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919054"
---
# <a name="adding-extensions-to-dsl-definitions"></a>DSL Tanımlarına Uzantılar Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL tanımı uzantısı, etki alanına özgü dil (DSL) için Uzantı paketi oluşturmanıza olanak sağlar. Bir Visual Studio Tümleştirme Uzantısı 'nda (VSıX) bulunan DSL uzantısı, bir kullanıcının bilgisayarına DSL ile aynı şekilde yüklenebilir. Ek özellikler dinamik olarak etkinleştirilebilir ve çalışma zamanında devre dışı bırakılabilir. DSLs 'in uzantı için açıkça tasarlanmaları gerekmez ve uzantılar, genişletilmiş DSL 'yi değiştirmeksizin daha sonra veya üçüncü taraflarca tasarlanabilir.

 Ek özellikler şunlar olabilir:

- Model ve sunum öğelerinin özellikleri

- Şekiller ve bağlayıcılar için dekoratörler

- Sınıflar, ilişkiler, şekiller ve bağlayıcılar

- Doğrulama kısıtlamaları

- Araç kutusu öğeleri ve sekmeleri

  Genişletilmiş bir DSL kullanıcısı ek özelliklerin örneklerini içeren bir model oluşturup kaydedebilir ve bunlar uygun uzantıyı yüklemiş olan diğer kullanıcılar tarafından okunabilir. Uzantıyı yüklememiş kullanıcılar ek özellikleri kullanamaz, ancak ek özellikleri kaybetmeden bir modeli güncelleştirebilir ve kaydedebilir.

  Örnek kod ve bu özellik hakkında daha fazla bilgi için bkz. [Visual Studio görselleştirme ve modelleme SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148) Web sitesi.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio görselleştirme ve modelleme SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148)
