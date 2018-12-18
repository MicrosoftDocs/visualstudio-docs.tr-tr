---
title: Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler Yürüt
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 34cf76adc56078303352bef9f01cef5ba774e2be
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921611"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler Yürüt

Verilere bağlı denetimler değerlerde düzenlerken, kullanıcılar güncelleştirilmiş değeri denetimin bağlı olduğu temel alınan veri kaynağına kaydetmek için geçerli kayıt kapalı gitmeniz gerekir. Öğelerden sürüklediğinizde [veri kaynakları penceresi](add-new-data-sources.md) bir forma bıraktığınız ilk öğe koda oluşturur **kaydetmek** düğmesini olayı <xref:System.Windows.Forms.BindingNavigator>. Bu kod çağırır <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi <xref:System.Windows.Forms.BindingSource>. Bu nedenle, çağrısına <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi yalnızca ilk için oluşturulan <xref:System.Windows.Forms.BindingSource> forma eklenir.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> Çağrısı işleminde şu anda düzenlenmekte olan tüm verilere bağlı denetimler değişiklikleri kaydeder. Odak ve bu nedenle, bir veri bağlama denetimi hala varsa tıklatın **kaydetmek** denetim kaydedilir, gerçek kaydetme önce bekleyen tüm düzenlemeleri düğmesine ( `TableAdapterManager.UpdateAll` yöntemi).

Verileri kaydetme bir parçası olarak değişiklikleri kaydetmeden kaydetmek bir kullanıcı çalışırsa bile, değişiklikleri, otomatik olarak gerçekleştirmeyi uygulamanızı yapılandırabilirsiniz işlemi.

> [!NOTE]
> Tasarımcı ekler `BindingSource.EndEdit` kod yalnızca ilk öğe için bir forma bırakıldı. Bu nedenle, bir çağırmak için kod satırı eklemeniz gerekir <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi her <xref:System.Windows.Forms.BindingSource> form üzerinde. Çağrılacak kod satırı el ile ekleyebilirsiniz <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi her <xref:System.Windows.Forms.BindingSource>. Alternatif olarak, ekleyebileceğiniz `EndEditOnAllBindingSources` forma yöntemi ve kaydetme gerçekleştirmeden önce çağırın.

Aşağıdaki kod bir [LINQ (dil ile tümleşik sorgu)](/dotnet/csharp/linq/) tüm yinelemek için sorgu <xref:System.Windows.Forms.BindingSource> bileşenleri ve çağrı <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi her <xref:System.Windows.Forms.BindingSource> bir form üzerinde.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Formdaki tüm BindingSource bileşenleri EndEdit çağrısı yapmak için

1.  Aşağıdaki kodu içeren formun ekleyin <xref:System.Windows.Forms.BindingSource> bileşenleri.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Kod form verilerini kaydetmek için tüm çağrıları hemen önce aşağıdaki satırı ekleyin ( `TableAdapterManager.UpdateAll()` yöntemi):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)