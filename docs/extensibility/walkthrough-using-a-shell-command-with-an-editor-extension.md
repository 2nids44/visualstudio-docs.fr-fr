---
title: "Procédure pas à pas : Utilisant une invite de commandes avec une Extension de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: 46
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 14ac62df46d3edaa93a18d5d2a2e717c7f0ba2de
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>Procédure pas à pas : Utilisant une invite de commandes avec une Extension de l’éditeur
Dans un VSPackage, vous pouvez ajouter des fonctionnalités telles que les commandes de menu à l’éditeur. Cette procédure pas à pas montre comment ajouter un ornement à un affichage de texte dans l’éditeur en appelant une commande de menu.  
  
 Cette procédure pas à pas illustre l’utilisation d’un VSPackage avec un composant Managed Extensibility Framework (MEF). Vous devez utiliser un VSPackage pour inscrire la commande de menu avec le shell Visual Studio, et vous pouvez utiliser la commande pour accéder à la partie du composant MEF.  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Création d’une Extension avec une commande de Menu  
 Créez un VSPackage qui place une commande de menu nommée **ajouter un ornement** sur la **outils** menu.  
  
1.  Créez un projet VSIX c# nommé `MenuCommandTest`et ajouter un nom de modèle d’élément commande personnalisée **AddAdornment**. Pour plus d’informations, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Une solution nommée MenuCommandTest s’ouvre. Le fichier MenuCommandTestPackage a le code qui crée la commande de menu et le place le **outils** menu. À ce stade, la commande génère simplement une boîte de message à afficher. Les étapes suivantes montrent comment modifier cette option pour afficher l’ornement de commentaire.  
  
3.  Ouvrez le fichier source.extension.vsixmanifest dans l’éditeur de manifeste VSIX. Le `Assets` onglet doit avoir une ligne pour un Microsoft.VisualStudio.VsPackage nommé MenuCommandTest.  
  
4.  Enregistrez et fermez le fichier Source.extension.vsixmanifest.  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>Ajout d’une Extension MEF pour l’Extension de commande  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nœud solution, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**. Dans le **ajouter un nouveau projet** boîte de dialogue, cliquez sur **extensibilité** sous **Visual C#**, puis **projet VSIX**. Attribuez un nom au projet `CommentAdornmentTest`.  
  
2.  Étant donné que ce projet interagissent avec le VSPackage assembly avec nom fort, vous devez signer l’assembly. Vous pouvez réutiliser le fichier de clé déjà créé pour l’assembly VSPackage.  
  
    1.  Ouvrez les propriétés du projet et sélectionnez le **signature** onglet.  
  
    2.  Sélectionnez **signer l’assembly**.  
  
    3.  Sous **choisir un fichier de clé de nom fort**, sélectionnez le fichier Key.snk qui a été généré pour l’assembly MenuCommandTest.  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>Qui fait référence à l’Extension MEF dans le projet VSPackage  
 Étant donné que vous ajoutez un composant MEF pour le VSPackage, vous devez spécifier les deux types de ressources dans le manifeste.  
  
> [!NOTE]
>  Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Pour faire référence au composant MEF dans le projet VSPackage  
  
1.  Dans le projet MenuCommandTest, ouvrez le fichier source.extension.vsixmanifest dans l’éditeur de manifeste VSIX.  
  
2.  Sur le **actifs** , cliquez sur **nouveau**.  
  
3.  Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
4.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
5.  Dans le **projet** , choisissez **CommentAdornmentTest**.  
  
6.  Enregistrez et fermez le fichier source.extension.vsixmanifest.  
  
7.  Assurez-vous que le projet de MenuCommandTest contient une référence au projet CommentAdornmentTest.  
  
8.  Dans le projet CommentAdornmentTest, définissez le projet pour produire un assembly. Dans le **l’Explorateur de solutions**, sélectionnez le projet et rechercher dans le **propriétés** fenêtre pour le **une sortie de génération copie à OutputDirectory** propriété et affectez-lui la valeur **true**.  
  
## <a name="defining-a-comment-adornment"></a>Définition d’un ornement de commentaire  
 L’ornement commentaire elle-même se compose d’un <xref:Microsoft.VisualStudio.Text.ITrackingSpan>qui suit le texte sélectionné et des chaînes qui représentent l’auteur et la description du texte.</xref:Microsoft.VisualStudio.Text.ITrackingSpan>  
  
#### <a name="to-define-a-comment-adornment"></a>Pour définir un ornement de commentaire  
  
1.  Dans le projet CommentAdornmentTest, ajoutez un nouveau fichier de classe et nommez-le `CommentAdornment`.  
  
2.  Ajoutez les références suivantes :  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  Ajoutez le code suivant `using` instruction.  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  Le fichier doit contenir une classe nommée `CommentAdornment`.  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5.  Ajoutez trois champs à la `CommentAdornment` de classe pour le <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, l’auteur et la description.</xref:Microsoft.VisualStudio.Text.ITrackingSpan>  
  
    ```c#  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  Ajoutez un constructeur qui initialise les champs.  
  
    ```c#  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="creating-a-visual-element-for-the-adornment"></a>Création d’un élément visuel pour l’ornement  
 Vous devez également définir un élément visuel pour votre ornement. Pour cette procédure pas à pas, définissez un contrôle qui hérite de la classe de Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.</xref:System.Windows.Controls.Canvas>  
  
1.  Créez une classe dans le projet CommentAdornmentTest et nommez-le `CommentBlock`.  
  
2.  Ajoutez les instructions `using` suivantes.  
  
    ```c#  
    using Microsoft.VisualStudio.Text;  
    using System;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Media;  
    using System.Windows.Shapes;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Rendre le `CommentBlock` classe hérite de <xref:System.Windows.Controls.Canvas>.</xref:System.Windows.Controls.Canvas>  
  
    ```c#  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  Ajoutez des champs privés pour définir les aspects visuels de l’ornement.  
  
    ```c#  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  Ajoutez un constructeur qui définit l’ornement de commentaire et ajoute le texte de votre choix.  
  
    ```c#  
    public CommentBlock(double textRightEdge, double viewRightEdge,   
            Geometry newTextGeometry, string author, string body)  
    {  
        if (brush == null)  
        {  
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));  
            brush.Freeze();  
            Brush penBrush = new SolidColorBrush(Colors.Green);  
            penBrush.Freeze();  
            solidPen = new Pen(penBrush, 0.5);  
            solidPen.Freeze();  
            dashPen = new Pen(penBrush, 0.5);  
            dashPen.DashStyle = DashStyles.Dash;  
            dashPen.Freeze();  
        }  
  
        this.textGeometry = newTextGeometry;  
  
        TextBlock tb1 = new TextBlock();  
        tb1.Text = author;  
        TextBlock tb2 = new TextBlock();  
        tb2.Text = body;  
  
        const int MarginWidth = 8;  
        this.commentGrid = new Grid();  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        ColumnDefinition cEdge = new ColumnDefinition();  
        cEdge.Width = new GridLength(MarginWidth);  
        ColumnDefinition cEdge2 = new ColumnDefinition();  
        cEdge2.Width = new GridLength(MarginWidth);  
        this.commentGrid.ColumnDefinitions.Add(cEdge);  
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());  
        this.commentGrid.ColumnDefinitions.Add(cEdge2);  
  
        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();  
        rect.RadiusX = 6;  
        rect.RadiusY = 3;  
        rect.Fill = brush;  
        rect.Stroke = Brushes.Green;  
  
            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);  
            tb1.Measure(inf);  
            tb2.Measure(inf);  
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);  
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;  
  
        Grid.SetColumn(rect, 0);  
        Grid.SetRow(rect, 0);  
         Grid.SetRowSpan(rect, 2);  
        Grid.SetColumnSpan(rect, 3);  
        Grid.SetRow(tb1, 0);  
        Grid.SetColumn(tb1, 1);  
        Grid.SetRow(tb2, 1);  
        Grid.SetColumn(tb2, 1);  
        this.commentGrid.Children.Add(rect);  
        this.commentGrid.Children.Add(tb1);  
        this.commentGrid.Children.Add(tb2);  
  
        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));  
         Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);  
  
        this.Children.Add(this.commentGrid);  
    }  
    ```  
  
6.  Également implémenter un <xref:System.Windows.Controls.Panel.OnRender%2A>Gestionnaire d’événements qui dessine l’ornement.</xref:System.Windows.Controls.Panel.OnRender%2A>  
  
    ```c#  
    protected override void OnRender(DrawingContext dc)  
    {  
        base.OnRender(dc);  
        if (this.textGeometry != null)  
        {  
            dc.DrawGeometry(brush, solidPen, this.textGeometry);  
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);  
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);  
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);  
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);  
            dc.DrawLine(dashPen, p1, p2);  
            dc.DrawLine(dashPen, p2, p3);  
        }  
    }  
    ```  
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>Ajout d’un IWpfTextViewCreationListener  
 Le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>est un composant MEF que vous pouvez utiliser pour écouter pour afficher les événements de création.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>  
  
1.  Ajoutez un fichier de classe au projet CommentAdornmentTest et nommez-le `Connector`.  
  
2.  Ajoutez les instructions `using` suivantes.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>des « text » et un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> </xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> L’attribut de type de contenu spécifie le type de contenu auquel s’applique le composant. Le type de texte est le type de base pour tous les types de fichier non binaire. Par conséquent, presque chaque vue de texte qui est créé sera de ce type. L’attribut de rôle de vue de texte spécifie le type d’affichage de texte à laquelle s’applique le composant. Rôles d’affichage de document texte généralement affichent le texte qui est composé de lignes et est stocké dans un fichier.  
  
     [!code-vb[VSSDKMenuCommandTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb) ] 
     [!code-cs [VSSDKMenuCommandTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  Implémentez le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>afin qu’il appelle la méthode statique (méthode) `Create()` événements du `CommentAdornmentManager`.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  Ajoutez une méthode que vous pouvez utiliser pour exécuter la commande.  
  
    ```c#  
    static public void Execute(IWpfTextViewHost host)  
    {  
        IWpfTextView view = host.TextView;  
        //Add a comment on the selected text.   
        if (!view.Selection.IsEmpty)  
        {  
            //Get the provider for the comment adornments in the property bag of the view.  
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));  
  
            //Add some arbitrary author and comment text.   
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;  
            string comment = "Four score....";  
  
            //Add the comment adornment using the provider.  
            provider.Add(view.Selection.SelectedSpans[0], author, comment);  
        }  
    }  
    ```  
  
## <a name="defining-an-adornment-layer"></a>Définition d’une couche d’ornement  
 Pour ajouter un ornement de nouveau, vous devez définir une couche d’ornement.  
  
#### <a name="to-define-an-adornment-layer"></a>Pour définir une couche d’ornement  
  
1.  Dans le `Connector` classe, déclarez un champ public de type <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>qui spécifie un nom unique pour la couche d’ornement et un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>qui définit la relation de l’ordre de cette couche d’ornement pour les autres couches de mode texte (texte, du signe insertion et sélection).</xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>Fournissant des ornements de commentaire  
 Lorsque vous définissez un ornement, également implémenter un fournisseur d’ornement de commentaire et un gestionnaire d’ornement de commentaire. Le fournisseur d’ornements commentaire conserve une liste des motifs de commentaire, écoute <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>événements dans la mémoire tampon sous-jacente, motifs de commentaire des suppressions lorsque le texte est supprimé.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
1.  Ajoutez un nouveau fichier de classe au projet CommentAdornmentTest et nommez-le `CommentAdornmentProvider`.  
  
2.  Ajoutez les instructions `using` suivantes.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  Ajoutez une classe nommée `CommentAdornmentProvider`.  
  
    ```c#  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  Ajoutez des champs privés pour la mémoire tampon de texte et la liste des motifs de commentaire liés à la mémoire tampon.  
  
    ```c#  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  Ajoutez un constructeur pour `CommentAdornmentProvider`. Ce constructeur doit avoir un accès privé, car le fournisseur est instancié par le `Create()` (méthode). Le constructeur ajoute les `OnBufferChanged` Gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>événements.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
    ```c#  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  Ajoutez la méthode `Create()`.  
  
    ```c#  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  Ajoutez la méthode `Detach()`.  
  
    ```c#  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  Ajouter la `OnBufferChanged` Gestionnaire d’événements.  
  
    ```c#  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-cs[VSSDKMenuCommandTest n °&21;](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs) ] 
     [!code-vb [VSSDKMenuCommandTest n °&21;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. Ajoutez une déclaration pour un `CommentsChanged` événement.  
  
    ```c#  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Créer un `Add()` pour ajouter l’ornement.  
  
    ```c#  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
        //Create a comment adornment given the span, author and text.  
        CommentAdornment comment = new CommentAdornment(span, author, text);  
  
        //Add it to the list of comments.   
        this.comments.Add(comment);  
  
        //Raise the changed event.  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
        if (commentsChanged != null)  
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));  
    }  
  
    ```  
  
11. Ajouter un `RemoveComments()` (méthode).  
  
    ```c#  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith.   
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
            {  
                //Raise the change event to delete this comment.   
                if (commentsChanged != null)  
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));  
            }  
            else  
                keptComments.Add(comment);  
        }  
  
        this.comments = keptComments;  
    }  
    ```  
  
12. Ajouter un `GetComments()` méthode qui retourne tous les commentaires dans une étendue d’instantanés donné.  
  
    ```c#  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. Ajoutez une classe nommée `CommentsChangedEventArgs`, comme suit.  
  
    ```c#  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="managing-comment-adornments"></a>Gestion des ornements de commentaire  
 Le Gestionnaire d’ornement commentaire crée l’ornement et l’ajoute à la couche d’ornement. Il écoute le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>événements afin qu’elles peuvent déplacer ou supprimer l’ornement.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Il écoute également le `CommentsChanged` événement est déclenché par le fournisseur d’ornements de commentaire lorsque les commentaires sont ajoutés ou supprimés.  
  
1.  Ajoutez un fichier de classe au projet CommentAdornmentTest et nommez-le `CommentAdornmentManager`.  
  
2.  Ajoutez les instructions `using` suivantes.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  Ajoutez une classe nommée `CommentAdornmentManager`.  
  
    ```c#  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  Ajoutez des champs privés.  
  
    ```c#  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  Ajoutez un constructeur qui s’abonne le gestionnaire pour la <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>et <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>des événements, ainsi qu’à la `CommentsChanged` événements.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Le constructeur est privé, car le gestionnaire est instancié par la méthode statique `Create()` (méthode).  
  
    ```c#  
    private CommentAdornmentManager(IWpfTextView view)  
    {  
        this.view = view;  
        this.view.LayoutChanged += OnLayoutChanged;  
        this.view.Closed += OnClosed;  
  
        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");  
  
        this.provider = CommentAdornmentProvider.Create(view);  
        this.provider.CommentsChanged += OnCommentsChanged;  
    }  
    ```  
  
6.  Ajouter la `Create()` méthode qui obtient un fournisseur ou en crée un si nécessaire.  
  
    ```c#  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  Ajouter la `CommentsChanged` gestionnaire.  
  
    ```c#  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  Ajouter la <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>Gestionnaire.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>  
  
    ```c#  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Ajouter la <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>Gestionnaire.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        //Get all of the comments that intersect any of the new or reformatted lines of text.  
        List<CommentAdornment> newComments = new List<CommentAdornment>();  
  
        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.    
        //Use the latter to find the comments that intersect the new or reformatted lines of text.   
        foreach (Span span in e.NewOrReformattedSpans)  
        {  
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));  
        }  
  
        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not.   
        //Sort the list and skip duplicates.  
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });  
  
        CommentAdornment lastComment = null;  
        foreach (CommentAdornment comment in newComments)  
        {  
            if (comment != lastComment)  
            {  
                lastComment = comment;  
                this.DrawComment(comment);  
            }  
        }  
    }  
    ```  
  
10. Ajoutez la méthode privée qui dessine le commentaire.  
  
     [!code-cs[VSSDKMenuCommandTest&#35;](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs) ] 
     [!code-vb [VSSDKMenuCommandTest&#35;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>À l’aide de la commande de Menu pour ajouter l’ornement de commentaire  
 Vous pouvez utiliser la commande de menu pour créer un ornement de commentaire en implémentant la `MenuItemCallback` méthode du VSPackage.  
  
1.  Ajoutez les références suivantes au projet MenuCommandTest :  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  Ouvrez le fichier AddAdornment.cs et ajoutez le code suivant `using` instructions.  
  
    ```c#  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  Supprimez la méthode ShowMessageBox() et ajoutez le Gestionnaire de commande suivant.  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  Ajoutez le code pour obtenir la vue active. Vous devez obtenir le `SVsTextManager` du shell Visual Studio pour obtenir de l’actif `IVsTextView`.  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  Si cette vue de texte est une instance d’une vue de texte de l’éditeur, vous pouvez le convertir en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>interface, puis obtenez <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>et ses associés <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> Utilisez le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>pour appeler le `Connector.Execute()` méthode qui obtient le fournisseur d’ornements de commentaire et ajoute l’ornement.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Le Gestionnaire de commande doit ressembler à ceci :  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
        IVsUserData userData = vTextView as IVsUserData;  
         if (userData == null)  
        {  
            Console.WriteLine("No text view is currently open");  
                            return;  
        }  
        IWpfTextViewHost viewHost;  
        object holder;  
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;  
        userData.GetData(ref guidViewHost, out holder);  
        viewHost = (IWpfTextViewHost)holder;  
        Connector.Execute(viewHost);  
    }  
    ```  
  
6.  Définissez la méthode de AddAdornmentHandler comme gestionnaire pour la commande AddAdornment dans le constructeur AddAdornment.  
  
    ```c#  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
  
1.  Générez la solution et commencez le débogage. L’instance expérimentale doit apparaître.  
  
2.  Créer un fichier texte. Tapez du texte et sélectionnez-le.  
  
3.  Sur le **outils** menu, cliquez sur **appeler un ornement ajouter**. Une info-bulle doit être affichée sur le côté droit de la fenêtre texte et doit contenir du texte qui ressemble au texte suivant.  
  
     VotreNomUtilisateur  
  
     Fourscore...  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)