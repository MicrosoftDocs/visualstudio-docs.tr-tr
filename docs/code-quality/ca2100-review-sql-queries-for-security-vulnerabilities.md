---
title: 'CA2100: SQL sorgularını güvenlik açıkları için gözden geçirin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 69c8ba3b5cd30b71828a34c4b3dc8d7b4584b613
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859052"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: SQL sorgularını güvenlik açıkları için gözden geçirin

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir yöntem ayarlar <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> yönteme değişkeninden oluşturulmuş dize kullanarak özellik.

## <a name="rule-description"></a>Kural açıklaması

Bu kural, dize değişkeninin kullanıcı girişi içerdiğini varsayar. Kullanıcı girişi ile oluşturulan SQL komut dizesi, SQL enjeksiyon saldırılarına karşı savunmasız durumdadır. SQL ekleme saldırısına kötü niyetli bir kullanıcı sorgu tasarımını zarar verecek ya da temel alınan veritabanına yetkisiz erişim girişimi değiştiren bir giriş sağlar. Tipik teknikleri ekleme tek tırnak işareti veya kesme işareti SQL değişmez dize sınırlayıcısı olan içerir. SQL açıklama gösterir iki kısa çizgi; ve noktalı virgül, yeni bir komut izlediğini belirtir. Kullanıcı girişi sorgu, aşağıdakilerden birini bir parçası olması gerekiyorsa saldırı riskini azaltmak için verimliliği, sırasına göre listelenmiş.

- Bir saklı yordamı kullanın.

- Bir parametreli komut dizesi kullanın.

- Komut dizesi oluşturmadan önce hem tür hem de içerik için kullanıcı girişi doğrulayın.

Aşağıdaki .NET Framework türleri uygulayan <xref:System.Data.IDbCommand.CommandText%2A> özelliği veya özelliği bir dize bağımsız değişkeni ayarlamak oluşturucular sağlar.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> ve <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> ve <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> ve <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

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

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için parametreli bir sorgu kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Komut metni herhangi bir kullanıcı girişi içermiyorsa bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bir yöntemi gösterir `UnsafeQuery`, kural ve bir yöntem ihlal `SaferQuery`, karşılayan kural parametreli komut dizesi kullanarak.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Ayrıca bkz.
 [Güvenliğe Genel Bakış](/dotnet/framework/data/adonet/security-overview)