---
title: Statik yerel işlev yeniden düzenleme seçenekleri
description: Bir yerel işlevi statik hale getirmek ve işlev dışında tanımlanan değişkenleri işlevin bildirimine ve çağrılarına geçirmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8e85fcc96542b4f3538729aeb50a4e080c902657
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479894"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Statik yerel işlev yeniden düzenlemeler ve hızlı eylemler

Bu makalede, statik yerel işlevlerle ilgili iki üretkenlik özelliği özetlenmektedir. , Yerel bir işlevi statik hale getiren ve diğeri değişkenleri statik bir yerel işleve geçirmek için kod üreten hızlı bir eylem olan bir yeniden düzenleme işlemidir.

## <a name="make-local-function-static"></a>Yerel işlevi statik yap

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Yerel bir işlevi statik hale getirir ve işlevin dışında tanımlanan değişkenlerde işlevin bildirimine ve çağrılarına geçirir.

**Ne zaman:** Yerel işlevinizin statik olmasını ve tüm değişkenlerin işlev kapsamında tanımlanmasını istiyorsunuz.

**Neden:** Statik yerel işlevler okunabilirliği artırır: belirli bir kodun yalıtılmış olduğunu bilmek, anlaşılması, yeniden okunması ve yeniden kullanılması kolaylaşır. Statik yerel işlevler, bir sınıfın yalnızca tek bir yöntemde çağrılan statik bir işlevle kirletmesini engellemek için kapsam sağlar.

### <a name="how-to"></a>Nasıl yapılır

1. Giriş işaretini yerel işlev adına yerleştirin.

2. **CTRL** tuşuna basın + **.** (nokta) **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetikleyin.

   ![Yerel işlevi statik yap](media/make-local-function-static.png)

3. **Yerel ' static ' Işlevini yap** ' ı seçin.

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Değişkeni statik bir yerel işlevde açıkça geçir

Bu hızlı eylem şu şekilde geçerlidir:

- C#

**Ne:** Bir değişkeni açıkça yerel bir statik işleve geçirir.

**Ne zaman:** Yerel bir işlevin statik olmasını, ancak hala onun dışında başlatılan değişkenleri kullanmasını istiyorsunuz.

**Neden:** Statik yerel işlevlerin kullanılması yalnızca programın belirli bir bağlamında bildirilip belirtilebilecek ve çağrılabilecek olduğunu bildiğinden okuyucular için açıklama sağlar. Değişkenleri bu bağlam dışında tanımlama esnekliği sağlar, ancak yine de statik yerel işleve bağımsız değişken olarak geçirebilirsiniz.

### <a name="how-to"></a>Nasıl yapılır

1. Giriş işaretini statik yerel işlevde kullanıldığı değişkene yerleştirin.

2. **CTRL** tuşuna basın + **.** (nokta) **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetikleyin.

   ![Değişkeni statik yerel işlevde açıkça geçir](media/pass-variable-explicitly-static-local-function.png)

3. **Değişkeni yerel statik işlevde açıkça geçir** seçeneğini belirleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)