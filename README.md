# How to Autofit Item Height Based on Content in WPF TreeView?

This repository describes how to autofit item height based on content in [WPF TreeView](https://www.syncfusion.com/wpf-controls/treeview) (SfTreeView).

The `TreeView` allows adjusting height of items based on the content measured size while loaded by setting the `Height` argument with value returned from [QueryNodeSizeEventArgs.GetAutoFitNodeHeight](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs.html#Syncfusion_UI_Xaml_TreeView_QueryNodeSizeEventArgs_GetAutoFitNodeHeight) method.

#### XAML

``` xml
<syncfusion:SfTreeView x:Name="sfTreeView"
                       Margin="10"
                       QueryNodeSize="SfTreeView_QueryNodeSize"    
                       ExpandActionTrigger="Node"
                       ItemsSource="{Binding Menu}" />
```

#### C#

``` csharp
sfTreeView.QueryNodeSize += SfTreeView_QueryNodeSize;

private void SfTreeView_QueryNodeSize(object sender, Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs e)
{
    if (e.Node.Level == 0)
    {
        //Returns specified item height for items.
        e.Height = 30;
        e.Handled = true;
    }
    else
    {
        // Returns item height based on the content loaded.
        e.Height = e.GetAutoFitNodeHeight();
        e.Handled = true;
    }
}
```

![TreeView with modified the item height based on the content](ModifiedHeightBasedOnContent.png)