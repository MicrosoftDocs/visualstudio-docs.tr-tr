---
title: 'CA1806: yöntem sonuçlarını yoksaymayın | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9e6b7bdd99500f0be29c8101ef9993b565914300
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830593"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Yöntem sonuçlarını yoksaymayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Kategori|Microsoft.Usage|  
|Yeni Değişiklik|Bozucu olmayan|  
  
## <a name="cause"></a>Sebep  
 Bu uyarı için birkaç olası nedeni vardır:  
  
- Yeni bir nesne oluşturulur, ancak hiç kullanılmadı.  
  
- Oluşturur ve yeni bir dize döndüren bir yöntem olarak adlandırılır ve yeni bir dize hiçbir zaman kullanılmaz.  
  
- Bir HRESULT ya da hata kodunu döndüren bir COM veya P/Invoke yöntemi hiçbir zaman kullanılmaz. Kural Tanımı  
  
  Gereksiz nesne oluşturma ve kullanılmayan nesnenin ilişkili çöp toplama performansını düşürebilir.  
  
  Dizeleri sabittir ve yöntemleri String.ToUpper gibi bir dize yöntemi çağrılırken dizesinde örneğini değiştirmek yerine yeni bir örneğini döndürür.  
  
  HRESULT ya da hata kodu yoksayılıyor beklenmeyen davranışlara hata koşullarında ya da düşük kaynak koşulları yol açabilir.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Bir yöntemi hiçbir zaman kullanılmaz B nesnesinin yeni bir örneğini oluşturur, örneği bir bağımsız değişken olarak başka yönteme geçirin veya örneği bir değişkene atayın. Nesne oluşturma gereksizse kaldıramazsınız- veya -  
  
 Yöntemi bir B yöntemini çağırır, ancak B yöntemi döndüren yeni dize örneğinde kullanmaz. Örneği bir bağımsız değişken olarak başka yönteme geçirin, örneği bir değişkene atayın. Ya da gereksizse çağrısını kaldırın.  
  
 veya  
  
 Yöntem, yöntem A B yöntemini çağırır, ancak HRESULT kullanmaz veya hata kodu döndürür. Sonucu bir koşullu deyimde kullanın, sonucu bir değişkene atayın ya da başka yönteme bağımsız değişken olarak geçirin.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Nesne oluşturma işlemi bazı amaca hizmet eder sürece bu kuraldan bir uyarıyı bastırmayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çağıran String.Trim sonucunu yoksayar bir sınıfı gösterir.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki ihlali String.Trim sonucu geri çağrıldı değişken atanarak düzeltir.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturduğu bir nesne kullanmayan bir yöntemi gösterir.  
  
> [!NOTE]
>  Visual Basic'te bu ihlal oluşturulamayacak.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir nesne gereksiz oluşturulmasını kaldırarak önceki ihlali düzeltir.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yerel GetShortPathName yöntemi döndürür hata kodu yoksayar bir yöntemi gösterir.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki ihlali hata kodu denetimi ve arama başarısız olduğunda bir özel durum düzeltir.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]