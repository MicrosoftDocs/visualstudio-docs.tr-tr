---
title: Yöntem hızlı eylemine parametre ekleme
description: Bir yönteme, kullanıma göre otomatik olarak bir parametre eklemek ve bildirmek için hızlı bir eylem kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c1e623bea0eab4b45aec3d331864db49a2787f8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846354"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Hızlı eylem kullanarak bir yönteme parametre ekleme

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir yönteme, kullanıma göre otomatik olarak bir parametre eklemenizi sağlar.

**Ne zaman:** Yöntemine bir parametre eklemeniz ve bunu otomatik olarak doğru bir şekilde bildirmek istemeniz gerekir.

**Neden:** Metodu çağırmadan önce yöntemi bildirimine ekleyebilirsiniz, ancak bu özellik bir yöntem çağrısına göre otomatik olarak ekler.

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Yöntem çağrısına fazladan bir bağımsız değişken ekleyin.

   Bir kırmızı dalgalı çizgi, çağırdığınız yöntemin adı altında görünür.

2. Hızlı Eylemler menüsü görünene kadar işaretçinizi kırmızı dalgalı çizgi üzerine getirin. Hızlı Eylemler menüsünde **aşağı oku** seçin ve ardından **parametre Ekle ' yi [Yöntem]** seçin.

   ![Visual Studio 'da yönteme parametre ekleme hızlı eylem](media/add-parameter-to-method.png)

   > [!TIP]
   > Hızlı Eylemler menüsüne imlecinizi yöntem çağrısının satırına yerleştirerek ve sonra **CTRL** tuşuna basarak da erişebilirsiniz + **.** (nokta) veya dosya kenar boşluğunda ampul simgesini seçin.

   Visual Studio, yöntem bildirimine yeni parametreyi ekler.

> [!NOTE]
> Yöntemine başka çağrılar varsa, yeni eklenen parametre için bir bağımsız değişken belirtmedikleri için, bu hızlı eylemi kullandıktan sonra hatalar üretebilirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucuya parametre Ekle](generate-constructor.md#addparameter)
