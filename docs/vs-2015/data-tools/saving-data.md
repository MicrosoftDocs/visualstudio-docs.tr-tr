---
title: Verileri kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: dc671d60ff37e9853dc64a62cbc1b91a6914e0e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249307"
---
# <a name="saving-data"></a>Verileri Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verileri kaydetme kalıcı yapma işlemi özgün veri deposunda, genellikle SQL Server gibi ilişkisel bir veritabanı için geri uygulamanın veri modelinde veri değiştirilmiş olur.  
  
 Bir veri modeli kullanarak bir veri kaynağını güncelleştirme genellikle iki adımlı bir işlemdir. İlk adım, yeni bilgilerle veri modelini güncelleştirme olarak — yeni kayıtlar değişmiş olan kayıtları ya da kayıtları silinir. İkinci adım veri modelinizde veritabanına değişiklikleri kaydetmektir.  
  
 Aşağıdaki konular, kavramlar ve verileri kaydetme ile ilgili görevleri açıklar.  
  
## <a name="related-topics"></a>İlgili Konular  
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)  
 Bir veri kümesinde değişiklikleri nasıl yapılacağını ve nasıl veri kümesi bu değişiklikleri veritabanına kaydetmek için değişiklikler hakkındaki bilgileri izler genel bakış sağlar.  
  
 [Varlık verilerini kaydetme](../data-tools/saving-entity-data.md)  
 Değişiklikleri Kaydet açıklar [ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205) ve [WCF Veri Hizmetleri 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) uygulamalar.