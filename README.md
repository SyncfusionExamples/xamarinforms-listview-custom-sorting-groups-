# xamarinforms-listview-custom-sorting-groups-
Xamarin Forms ListView provides support to sort the groups using Comparer.

## Sample

```xaml
<sync:SfListView x:Name="listView"
                    ItemSize="70" 
                    FocusBorderThickness="0"
                    IsStickyGroupHeader="True"
                    AllowGroupExpandCollapse="True"
                    GroupHeaderSize="40"
                    ItemsSource="{Binding ContactsInfo}">

    <sync:SfListView.DataSource>
        <dataSource:DataSource>
            <dataSource:DataSource.GroupDescriptors>
                <dataSource:GroupDescriptor PropertyName="ContactType">
                    <dataSource:GroupDescriptor.Comparer>
                        <local:CustomGroupComparer/>
                    </dataSource:GroupDescriptor.Comparer>
                </dataSource:GroupDescriptor>
            </dataSource:DataSource.GroupDescriptors>
        </dataSource:DataSource>
    </sync:SfListView.DataSource>

    <sync:SfListView.GroupHeaderTemplate>
        <DataTemplate>
            <ViewCell>
                <ViewCell.View>
                <Label Text="{Binding Key}" />
                    <code>
                    . . .
                    . . .
                    <code>
                </ViewCell.View>
            </ViewCell>
        </DataTemplate>
    </sync:SfListView.GroupHeaderTemplate>

    <sync:SfListView.ItemTemplate>
        <DataTemplate>
            <ViewCell>
                <ViewCell.View>
                    <Grid x:Name="grid" RowSpacing="0">
                        <Grid.RowDefinitions>
                            <RowDefinition Height="*" />
                            <RowDefinition Height="1" />
                        </Grid.RowDefinitions>
                        <Grid RowSpacing="0">
                            <Grid.ColumnDefinitions>
                                <ColumnDefinition Width="70" />
                                <ColumnDefinition Width="*" />
                                <ColumnDefinition Width="Auto" />
                            </Grid.ColumnDefinitions>
                            <code>
                            . . .
                            . . .
                            <code>
                    </Grid>
                </ViewCell.View>
            </ViewCell>
        </DataTemplate>
    </sync:SfListView.ItemTemplate>
</sync:SfListView>

CustomGroupComparer:
public class CustomGroupComparer : IComparer<GroupResult>
{
    public int Compare(GroupResult x, GroupResult y)
    {
        if (x.Count > y.Count)
        {
            return 1;
        }
        else if (x.Count < y.Count)
        {
            return -1;
        }

        return 0;
    }
}
```