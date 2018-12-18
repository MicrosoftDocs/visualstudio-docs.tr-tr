---
title: Silme davranışını özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 401458a33c67d0c8d0302fddcdfd988113101e28
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837572"
---
# <a name="customizing-deletion-behavior"></a>Silme Davranışını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genellikle bir öğeyi silme ilgili öğeleri de silinmesine neden olur. Tüm ilişkiler bağlı ve herhangi bir alt öğe silindi. Bu davranış adlı *yayma Sil*. Örneğin ek ilgili öğeler silinir düzenlemek delete yayma özelleştirebilirsiniz. Program kodunu yazarak silme yayma model durumuna bağlı yapabilirsiniz. Ayrıca, yanıt bir silme işlemi için başka değişiklik neden olabilir.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Varsayılan silme davranışı](#default)  
  
-   [Bir rolün yaymak Sil seçeneği ayarlama](#property)  
  
-   [Geçersiz kılma Sil kapanış](#closure) – silme komşu öğeleri silme işlemini burada neden olabilir, bu tekniği kullanın.  
  
-   [OnDeleting ve OnDeleted kullanarak](#ondeleting) – yanıt burada bir değer içinde veya dışında depolama güncelleştirme gibi eylemler dahil olabilir, bu yöntemleri kullanın.  
  
-   [Silme kuralları](#rules) – burada bir değişiklik neden olabilir başkalarına depo içindeki herhangi bir türdeki güncelleştirmeleri yaymak için kuralları kullanın.  
  
-   [Silme işlemi olayları](#rules) – örneğin diğer için depo dışında güncelleştirmeleri yayılması kullan deposu olayları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belgeleri.  
  
-   [Birleştirme](#unmerge) – birleştirme işlemi bir alt öğesi üst göreve bağlı birleştirme işlemi geri alın.  
  
##  <a name="default"></a> Varsayılan silme davranışı  
 Varsayılan olarak, aşağıdaki kurallar silme yayma yöneten:  
  
-   Bir öğe silinirse, tüm katıştırılmış öğeleri de silinir. Katıştırılmış öğeleri bu öğe kaynağı olduğu ilişkileri ekleme hedefleri olanla aynıdır. Örneğin, bir gömme ilişkisi ise **albüm** için **şarkı**, belirli bir albümü silindiğinde, tüm şarkıları da silinir.  
  
     Aksine, bir şarkı sildiğinizde albümü silinmez.  
  
-   Varsayılan olarak, silme işlemi başvuru ilişkileri dağıtılmaz. Başvuru ilişkisi varsa **ArtistPlaysOnAlbum** gelen **albüm** için **sanatçının**albüm silinmesi tüm ilgili sanatçının silinmez ve bir sanatçıdan silme yok Tüm albüm silin.  
  
     Ancak, silme işlemi yerleşik bazı ilişkiler yayar. Örneğin, bir model öğesi silindiğinde, diyagram üzerinde şeklini de silinir. Öğesi ve şekli ile ilgili `PresentationViewsSubject` başvuru ilişkisi.  
  
-   Öğesi, kaynak veya hedef rol ya da bağlı her ilişki silinir. Karşı rol öğe rolü özelliği, artık silinen öğe içerir.  
  
##  <a name="property"></a> Bir rolün yaymak Sil seçeneği ayarlama  
 Silme katıştırılmış bir alt, üst veya başvuru ilişkisi boyunca yayılmasına neden olabilir.  
  
#### <a name="to-set-delete-propagation"></a>Delete yayma ayarlamak için  
  
1. DSL tanım diyagramı üzerinde seçin *rol* yayma silmek istediğiniz. Rol satırı soldaki veya bir etki alanı ilişkisi kutusunun sağ tarafından temsil edilir.  
  
    Örneğin, albüm silindiğinde belirtmek istiyorsanız, ilgili sanatçıların da silinir ve ardından etki alanı sınıfı sanatçının bağlı rolü seçin.  
  
2. Özellikler penceresinde ayarlayın **yayar Sil** özelliği.  
  
3. F5 tuşuna basın ve doğrulayın:  
  
   -   Bu ilişkinin örneğini silindiğinde, seçili rolü öğe de silinecek.  
  
   -   Karşı rol bir öğe silindiğinde, bu ilişki örneklerini silinecek ve ilgili öğeleri Bu roldeki silinecek.  
  
   Ayrıca bkz **yayar Sil** seçeneğini **DSL ayrıntıları** penceresi. Bir etki alanı sınıfı seçin ve açın DSL Ayrıntıları penceresinde **silme davranışı** penceresinin tarafındaki düğmeye tıklayarak sayfası. **Yay** seçeneği her ilişkinin end'in role gösterilir. **Silme Style** sütununda olmadığını **yay** varsayılan ayarında seçenektir ancak ayrı hiçbir etkisi yok.  
  
## <a name="delete-propagation-by-using-program-code"></a>Program kodu kullanarak yayma Sil  
 DSL tanımı dosyasında seçenekleri yalnızca için hemen bir komşu silme işlemi yayar olmadığını seçmenize olanak tanır. Daha karmaşık bir delete yayma düzenini uygulamak için program kodu yazabilirsiniz.  
  
> [!NOTE]
>  Program kodu için DSL tanımını eklemek için ayrı bir kod dosyasında oluşturma **Dsl** proje ve oluşturulan kod klasörü sınıfları genişletmek için kısmi tanımları yazma. Daha fazla bilgi için [bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
##  <a name="closure"></a> Bir silme kapanış tanımlama  
 Silme işlemi sınıfın kullandığı _YourModel_**DeleteClosure** , bir başlangıç seçimi silmek için hangi öğelerin belirlemek için. Çağrı `ShouldVisitRelationship()` ve `ShouldVisitRolePlayer()` tekrar tekrar ilişkilerin grafik yürüyen. Bu yöntemleri geçersiz kılabilirsiniz. ShouldVisitRolePlayer bağlantı ve bağlantının rollerden biri öğe kimliği ile sağlanır. Aşağıdaki değerlerden birini döndürmesi gerekir:  
  
-   **VisitorFilterResult.Yes**: öğenin silinmesi gerekir ve walker denemeye devam öğe kullanıcının diğer bağlantılar.  
  
-   **VisitorFilterResult.DoNotCare** – başka bir sorgu, silinmesi gerektiğini yanıtlar sürece öğe silinmemelidir.  
  
-   **VisitorFilterResult.Never** – başka bir sorgu yanıtları bile öğesi, silinmemelidir **Evet**, ve walker değil denemelisiniz öğe kullanıcının diğer bağlantılar.  
  
```  
// When a musician is deleted, delete their albums with a low rating.  
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs  
partial class MusicLibDeleteClosure  
{  
  public override VisitorFilterResult ShouldVisitRolePlayer  
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,   
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)  
  {  
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;  
    if (link != null   
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)  
    {  
      // Count other unvisited links to the Album of this link.  
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)  
              .Where(linkAlbumArtist =>   
                     linkAlbumArtist != link &&  
                     !walker.Visited(linkAlbumArtist))  
              .Count() == 0)  
      {  
        // Should delete this role player:  
        return VisitorFilterResult.Yes;   
      }  
      else  
        // Don’t delete unless another relationship deletes it:  
        return VisitorFilterResult.DoNotCare;   
    }  
    else   
    {  
      // Test for and respond to other relationships and roles here.  
  
      // Not the relationship or role we’re interested in.  
      return base.ShouldVisitRolePlayer(walker, sourceElement,   
             elementLink, targetDomainRole, targetRolePlayer);  
    }  
  }  
}  
  
```  
  
 Öğeleri ve bağlantılarına silinecek kümesini silme işlemi başlamadan önce belirlenir kapanış teknik sağlar. Walker, kapanış sonuçlarını modelinin diğer kısımlarından olanla aynı zamanda birleştirir.  
  
 Ancak, teknik silme yalnızca Komşuları ilişkilerinin graftaki etkiler varsayar: başka bir modelin parçası içindeki bir öğeyi silmek için bu yöntemi kullanamazsınız. Öğeleri ekleme veya silme işlemi için yanıt başka değişiklikler yapmak istiyorsanız kullanamazsınız.  
  
##  <a name="ondeleting"></a> OnDeleting ve OnDeleted kullanma  
 Geçersiz kılabilirsiniz `OnDeleting()` veya `OnDeleted()` bir etki alanı sınıfı veya bir etki alanı ilişkisi.  
  
1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> silinmek üzere bir öğe olduğunda, ancak ilişkilerini kesilmeden çağrılır. Diğer öğeleri gelen ve giden hala gezinebilir ve hala `store.ElementDirectory`.  
  
    Aynı anda birkaç öğe silindiğinde, OnDeleting hepsi için silme gerçekleştirmeden önce çağrılır.  
  
    `IsDeleting` geçerlidir.  
  
2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> öğe silindiğinde çağırılır. Böylece gerekirse geri alma gerçekleştirilebilir, ancak diğer öğelerden bağlantısı kesilmişse ve kaldırılmasını CLR yığınında kalır `store.ElementDirectory`. İlişki için roller hala eski rol oyuncuları başvuru.`IsDeleted` geçerlidir.  
  
3. Kullanıcının bir öğenin oluşturduktan sonra geri çağırır ve önceki bir silme işlemi Yinele için tekrarlandığında OnDeleting ve OnDeleted adı verilir. Kullanım `this.Store.InUndoRedoOrRollback` bu gibi durumlarda mağazası öğeleri güncelleştirme önlemek için. Daha fazla bilgi için [nasıl yapılır: modeli güncelleştirmek için kullanım işlemleri](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
   Örneğin, son alt şarkı silindiğinde aşağıdaki kod, albüm siler:  
  
```  
  
// Delete the parent Album when the last Song is deleted.  
// Override methods in the embedding relationship between Album and Song:  
partial class AlbumHasSongs  
{  
  protected override void OnDeleted()  
  {  
    base.OnDeleted();  
    // Don't perform in-store actions in undo:  
    if (this.Store.InUndoRedoOrRollback) return;  
    // Relationship source and target still work:  
    // Don't bother if source is already on its way out:  
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)  
    {  
      if (this.Album.Songs.Count == 0)  
      {   
        this.Album.Delete();  
} } } }  
  
```  
  
 Daha fazla genellikle olduğu yararlı tetikleyici ilişkisinin rolünü öğeden silinmeye karşı öğe silindiğinde bu hem de çalıştığından ve ilişki silindiğinde. Ancak, bir başvuru ilişkisi için ilgili bir öğe silindiğinde ancak ilişki silinmez silme işlemi yayar isteyebilirsiniz. Bu örnekte, son katkıda bulunan sanatçının silinmiş, ancak silinen ilişkiler, yanıtlamıyor albüm siler:  
  
```  
using System.Linq; ...  
// Assumes a many-many reference relationship   
// between Artist and Album.    
partial class Artist  
{  
  protected override void OnDeleting()  
  {  
    base.OnDeleting();  
    if (this.Store.InUndoRedoOrRollback) return;  
    List<Album> toDelete = new List<Album>();  
    foreach (Album album in this.Albums)  
    {  
      if (album.Artists.Where(artist => !artist.IsDeleting)  
                        .Count() == 0)  
      {  
        toDelete.Add(album);  
      }  
    }  
    foreach (Album album in toDelete)  
    {  
      album.Delete();  
} } }  
  
```  
  
 Gerçekleştirirken <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> OnDeleting ve OnDeleted bir öğe üzerinde çağrılır. Bu her zaman gerçekleştirilen satır içi – diğer bir deyişle, hemen önce ve sonra gerçek silme yöntemlerdir. Kodunuzu iki veya daha fazla öğe silerse, OnDeleting ve OnDeleted tümünde değişim içinde sırayla çağrılır.  
  
##  <a name="rules"></a> Silme kuralları ve olaylar  
 OnDelete işleyiciler alternatif, silme kuralları ve silme olaylarını tanımlayabilirsiniz.  
  
1.  **Silme** ve **Sil** kuralları yalnızca bir işlemde ve bir geri alma veya yineleme içinde değil tetiklenir. Bunları silme gerçekleştirildiği işlem sonunda yürütmek için kuyruğa alınacak ayarlayabilirsiniz. Silme kuralları sırada olan tüm silinen kuralları önce her zaman yürütülür.  
  
     Yalnızca öğeleri ilişkileri, diyagram öğeleri ve özellikleri de dahil olmak üzere deposundaki etkileyen değişiklikleri yaymak için kuralları kullanın. Genellikle, silme kural silme yaymak için kullanılır ve bir Delete kural değiştirme öğeleri ve ilişkileri oluşturmak için kullanılır.  
  
     Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).  
  
2.  **Silinen** deposu olay, bir işlem sonunda çağrılır ve bir geri alma veya yineleme sonra çağrılır. Silme işlemleri deponun dosyaları, veritabanı girişlerini ya da diğer nesneleri dışındaki nesneler yaymak için bu nedenle kullanılabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Daha fazla bilgi için [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
    > [!WARNING]
    >  Bir öğe silindiğinde, etki alanı özellik değerlerine erişebilirsiniz, ancak ilişki bağlantılarını gidilemiyor. Ancak, silinen bir olay bir ilişkiye ayarlarsanız, kendi rol oyuncuları olan iki öğe de erişebilirsiniz. Bu nedenle, bir model öğesini silme işlemi için yanıt, ancak bağlı bir öğeye erişmeyi istediğiniz istiyorsanız, model öğesinin etki alanı sınıfı yerine ilişkiyi silme olayı ayarlayın.  
  
### <a name="example-deletion-rules"></a>Örnek silme kuralları  
  
```  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletingRule : DeletingRule  
{  
  public override void ElementDeleting(ElementDeletingEventArgs e)  
  {  
    base.ElementDeleting(e);  
    // ...perform tasks to propagate imminent deletion  
  }  
}  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletedRule : DeleteRule  
{  
  public override void ElementDeleted(ElementDeletedEventArgs e)  
  {  
    base.ElementDeleted(e);  
    // ...perform tasks such as creating new elements  
  }  
}  
  
// The rule must be registered:  
public partial class MusicLibDomainModel  
{  
  protected override Type[] GetCustomDomainModelTypes()  
  {  
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
    types.Add(typeof(AlbumDeletingRule));  
    types.Add(typeof(AlbumDeletedRule));  
    // If you add more rules, list them here.   
    return types.ToArray();  
  }  
}  
  
```  
  
### <a name="example-deleted-event"></a>Örnek olay silindi  
  
```  
partial class NestedShapesSampleDocData  
{  
  protected override void OnDocumentLoaded(EventArgs e)  
  {  
    base.OnDocumentLoaded(e);  
    DomainRelationshipInfo commentRelationship =   
          this.Store.DomainDataDirectory  
          .FindDomainRelationship(typeof(CommentsReferenceComponents));  
  
    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,  
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));  
  }  
  
  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)  
  {  
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;  
    Comment comment = link.Comment;  
    Component component = link.Subject;  
    if (comment.IsDeleted)  
    {  
      // The link was deleted because the comment was deleted.  
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);  
    }  
    else  
    {  
      // It was just the link that was deleted - the comment itself remains.  
      System.Windows.Forms.MessageBox.Show("Removed comment link to "   
           + component.Name);  
    }  
  }  
}  
  
```  
  
##  <a name="unmerge"></a> Çöz  
 Bir alt öğesi kendi üst öğesine iliştirir işlem çağrılır *birleştirme*. Yeni bir öğe olduğunda oluşur veya öğeler grubu araç kutusundan oluşturulan veya başka bir modelin parçası olarak taşınır veya panodan kopyalanır. Üst ve yeni alt öğe arasındaki gömme ilişkisi oluşturmanın yanı sıra, birleştirme işlemi de ek ilişkileri ayarlamanız yardımcı öğeleri oluşturmak ve öğesinde ayarlanan özellik değerleri. Birleştirme işlemi, bir öğe birleştirme yönergesi (EMD) içinde kapsüllenir.  
  
 Ayrıca bir EMD tamamlayıcı kapsülleyen *Çöz* veya `MergeDisconnect` işlemi. Bir birleştirme kullanarak oluşturulan bir küme öğe varsa, ilişkili kullanmak için önerilir tutarlı bir durumda kalan öğeleri bırakmak istiyorsanız, bu sınıftan bir öğe kaldırmak için bölme. Birleştirme işlemi genellikle önceki bölümlerde açıklanan teknikleri kullanır.  
  
 Daha fazla bilgi için [özelleştirme öğe oluşturma ve hareketini](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md)   
 [Öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md)   
 [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)



