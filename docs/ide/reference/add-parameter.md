---
title: Parametre için bir yöntem hızlı Eylem Ekle
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0337f9869764f544f5248d4da717af849457b8e8
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446788"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Hızlı bir eylem kullanarak bir yönteme bir parametre ekleyin

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** kullanımını temel alarak bir yöntem, otomatik olarak bir parametre eklemenizi sağlar.

**Ne zaman:** bir yönteme parametre eklemek ve düzgün bir şekilde otomatik olarak bildirmek istiyorsanız gerekir.

**Neden:** ancak bu özellik üzerinde bir yöntem çağrısının otomatik olarak temel ekler, çağırmadan önce yöntem bildiriminde için'parametre ekleyebilirsiniz.

## <a name="how-to-use-it"></a>Nasıl kullanılacağını

1. Ek bağımsız değişken bir yöntem çağrısını ekleyin.

   "Dalgalı" kırmızı, Çağırdığınız yöntemin adı altında görünür.

2. Hızlı Eylemler menüsü görünene kadar işaretçiyi üzerinde kırmızı "dalgalı" yerleştirin. Seçin **aşağı ok** seçin ve hızlı Eylemler menüsü **[method] için parametre Ekle**.

   ![Visual Studio'da hızlı eylem yöntemi için parametre Ekle](media/add-parameter-to-method.png)

   > [!TIP]
   > Yöntem çağrısı ve ardından ya basarak satırında imleci yerleştirerek hızlı Eylemler menüsünden erişebilirsiniz **Ctrl**+**.** ya da ampul simgesini seçerek dosya kenar boşluğunda.

   Visual Studio, yöntem bildiriminde için yeni bir parametre ekler.

> [!NOTE]
> Yöntemine yapılan diğer çağrılar varsa, bu hızlı eylem kullandıktan sonra yeni eklenen parametresi için bağımsız değişken belirtmezsiniz çünkü bunlar hataları üretebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucusuna parametre Ekle](generate-constructor.md#addparameter)