---
title: 'Nasıl yapılır: Yönetilen bir Kod Hatası için bir İş Öğesi Oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b251970bfd57b31842e1573e2e156e11a517c81a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279484"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Nasıl yapılır: Yönetilen bir Kod Hatası için bir İş Öğesi Oluşturma

Visual Studio içinden günlük iş öğesi iş öğesi izleme özelliğini kullanabilirsiniz. Bu özelliği kullanmak için projenizi bir Azure DevOps projesi içinde bir parçası olmalıdır [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Yönetilen kod hatası için bir iş öğesi oluşturmak için

1. İçinde **Kod Analizi** penceresinde uyarıyı seçin.

2. Seçin **eylemleri**, ardından **iş öğesi oluştur** ve oluşturulacak çalışma öğesi türünü seçin.

     Yeni bir iş öğesi, hata bilgilerini belirtmek oluşturulur.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Birden çok yönetilen kod kusurları için iş öğesi oluşturmak için

1. İçinde **hata listesi**, birden çok uyarıları seçin ve sonra uyarılar sağ tıklayın.

2. İşaret **iş öğesi oluştur** ve oluşturulacak çalışma öğesi türüne tıklayın.

     Tek bir iş öğesi, hata bilgilerini belirtmek seçilen tüm uyarılar oluşturulur.