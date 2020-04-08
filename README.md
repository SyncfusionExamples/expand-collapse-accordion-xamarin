# How to expand or collapse Accordion programmatically in Xamarin.Forms (SfAccordion)

You can programmatically expand or collapse the [AccordionItem](https://help.syncfusion.com/xamarin/accordion/bindablelayout?&_ga=2.123019343.576537389.1586149449-1204678185.1570168583#defining-the-accordionitem) in Xamarin.Forms [SfAccordion](https://help.syncfusion.com/xamarin/accordion/getting-started?) by binding the model property to [AccordionItem.IsExpanded](https://help.syncfusion.com/cr/cref_files/xamarin/Syncfusion.Expander.XForms~Syncfusion.XForms.Accordion.AccordionItem~IsExpanded.html?) property.

You can also refer the following article.

https://www.syncfusion.com/kb/11314/how-to-expand-or-collapse-accordion-programmatically-in-xamarin-forms-sfaccordion

**XAML**

IsExpanded model property is bound to IsExpanded property of AccordionItem to expand or collapse when update property value programmatically.

``` xml
<DataTemplate>
    <syncfusion:AccordionItem IsExpanded="{Binding IsExpand}">
        <syncfusion:AccordionItem.Header>
            <Grid HeightRequest="60">
                <Label Text="{Binding Name}" FontSize="Medium"/>
            </Grid>
        </syncfusion:AccordionItem.Header>
        <syncfusion:AccordionItem.Content>
            <Grid>
                <Grid>
                    <Grid.RowDefinitions>
                        <RowDefinition Height="50"/>
                        <RowDefinition Height="50"/>
                    </Grid.RowDefinitions>
                    <Label Text="{Binding Description}"/>
                    <Button x:Name="btn" Grid.Row="1" Text="{Binding Name}" Command="{Binding Path=BindingContext.ButtonCommand, Source={x:Reference Accordion}}" CommandParameter="{x:Reference btn}"/>
                </Grid>
            </Grid>
        </syncfusion:AccordionItem.Content>
    </syncfusion:AccordionItem>
</DataTemplate>
```

**C#**

OnExpandCollapse is used to change the IsExpand property to expand or collapse the item.

``` c#
public class ItemInfoRepository
{
    public Command<object> ExpandCollapse{ get; set; }
 
    public ItemInfoRepository()
    {
        ExpandCollapse= new Command<object>(OnExpandCollapse);
    }
    
    private void OnExpandCollapse (object obj)
    {
        var item = (obj as Button).BindingContext as ItemInfo;
        item.IsExpand = !item.IsExpand;
    }
}
```
