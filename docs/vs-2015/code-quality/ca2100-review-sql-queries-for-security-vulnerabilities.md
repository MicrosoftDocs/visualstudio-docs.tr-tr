---
title: 'CA2100: Gözden geçirme SQL sorgularını güvenlik açıkları için | Microsoft Docs'
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
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c77e448a492a64e3bbdf0f86809cdf82d7fd72fa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877406"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: SQL sorgularını güvenlik açıkları için gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir yöntem ayarlar <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> yönteme değişkeninden oluşturulmuş dize kullanarak özellik.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, dize değişkeninin kullanıcı girişi içerdiğini varsayar. Kullanıcı girişi ile oluşturulan SQL komut dizesi, SQL enjeksiyon saldırılarına karşı savunmasız durumdadır. SQL ekleme saldırısına kötü niyetli bir kullanıcı sorgu tasarımını zarar verecek ya da temel alınan veritabanına yetkisiz erişim girişimi değiştiren bir giriş sağlar. Tipik teknikleri ekleme tek tırnak işareti veya kesme işareti SQL değişmez dize sınırlayıcısı olan içerir. SQL açıklama gösterir iki kısa çizgi; ve noktalı virgül, yeni bir komut izlediğini belirtir. Kullanıcı girişi sorgu, aşağıdakilerden birini bir parçası olması gerekiyorsa saldırı riskini azaltmak için verimliliği, sırasına göre listelenmiş.

- Bir saklı yordamı kullanın.

- Bir parametreli komut dizesi kullanın.

- Komut dizesi oluşturmadan önce hem tür hem de içerik için kullanıcı girişi doğrulayın.

  Aşağıdaki [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] türleri uygulayan <xref:System.Data.IDbCommand.CommandText%2A> özelliği veya özelliği bir dize bağımsız değişkeni ayarlamak oluşturucular sağlar.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> ve <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> ve <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> ve <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System.Data.SqlServerCe.SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) ve [System.Data.SqlServerCe.SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> ve <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  ToString yöntemini bir türün açıkça veya dolaylı olarak kullanıldığında, bu kuralı ihlal ettiğini fark sorgu dizesi oluşturmak için. Bir örnek verilmiştir.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Kötü niyetli bir kullanıcı ToString() yöntemini geçersiz kılma nedeni kuralı ihlal edildi.

 ToString örtük olarak kullanıldığında kural ayrıca ihlal edildi.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için parametreli bir sorgu kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Komut metni herhangi bir kullanıcı girişi içermiyorsa bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bir yöntemi gösterir `UnsafeQuery`, kural ve bir yöntem ihlal `SaferQuery`, karşılayan kural parametreli komut dizesi kullanarak.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenliğe Genel Bakış](http://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)



