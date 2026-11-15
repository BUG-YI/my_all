# WPF

### MVVM

```cmd
#下载Mvvm框架模板
dotnet add package CommunityToolkit.Mvvm
```



HZMAPP/Models.User

```csharp
namespace HZMAPP.Models;

public class User
{
    public string? Username { get; set; }
    public string? Password { get; set; }
}
```

HZMAPP/ViewModels.LoginVM

```csharp
using System.Windows;
using CommunityToolkit.Mvvm.ComponentModel;
using CommunityToolkit.Mvvm.Input;

namespace HZMAPP.ViewModels;

public partial class LoginVM:ObservableObject
{
    [ObservableProperty] 
    private string username = "";

    [ObservableProperty] 
    private string password = "";

    [RelayCommand]
    private void Login()
    {
        if (Username.Equals("a") && Password.Equals("a"))
        {
            MessageBox.Show("success");
        }
        else
        {
            Username = "";
            Password = "";
            MessageBox.Show("failed");
        }
    }
}
```

HZMAPP/Views/LR/Login.xaml

```xaml
<Page x:Class="HZMAPP.Views.LR.Login"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:local="clr-namespace:HZMAPP.Views.LR"
      xmlns:vm="clr-namespace:HZMAPP.ViewModels"
      mc:Ignorable="d">
    
    <Page.DataContext>
        <vm:LoginVM/>
    </Page.DataContext>
    
    <Grid ShowGridLines="True">
        
        <Grid.RowDefinitions>
            <RowDefinition></RowDefinition>
            <RowDefinition></RowDefinition>
            <RowDefinition></RowDefinition>
            <RowDefinition></RowDefinition>
        </Grid.RowDefinitions>
        
        <TextBlock Text="Login" 
                   HorizontalAlignment="Center"
                   FontSize="37"/>
        <TextBox Grid.Row="1" Width="200" Height="50" Text="{Binding Username, UpdateSourceTrigger=LostFocus}"></TextBox>
        <PasswordBox Grid.Row="2" Width="200" Height="50" PasswordChanged="PasswordBox_OnPasswordChanged"></PasswordBox>
        <Button Grid.Row="3" Content="login" Command="{Binding LoginCommand}"></Button>
        
    </Grid>
</Page>
```

HZMAPP/Views/LR/Login.xaml.cs

```csharp
using System.Windows;
using System.Windows.Controls;
using HZMAPP.ViewModels;

namespace HZMAPP.Views.LR;

public partial class Login : Page
{
    public Login()
    {
        InitializeComponent();
    }

    private void PasswordBox_OnPasswordChanged(object sender, RoutedEventArgs e)
    {
        if (DataContext is LoginVM vm)
        {
            vm.Password = ((PasswordBox)sender).Password;
        }
    }
}
```

> [!note]
>
> PWF出于安全考虑用方法将数据传给modelvm模型



### 更改控件样式

```
<StackPanel.Resources>
    <Style TargetType="TextBlock">
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="TextBlock">
                    <Border CornerRadius="5"
                            BorderBrush="Aquamarine"
                            BorderThickness="1"
                            Background="Transparent"
                            Margin="10,0">
                        <ContentPresenter
                            HorizontalAlignment="Center"
                            VerticalAlignment="Center"></ContentPresenter>
                    </Border>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
</StackPanel.Resources>
```



### 项目.csproj配置

```
<!--将该路径下的图片打包进程序-->
<ItemGroup>
    <!-- 将 Assets 文件夹及其所有子文件夹下的所有图片，作为资源打包 -->
    <Resource Include="Assets\**\*.png" />
    <Resource Include="Assets\**\*.jpg" />
    <Resource Include="Assets\**\*.gif" />
</ItemGroup>
```



### User Control

将重复控件提取，使其能够复用

usercontrol.xaml

```xaml
<UserControl x:Class="HZMAPP.User_Controls.ItemsControl"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
             mc:Ignorable="d"
             x:Name="ItemsC"
             d:DesignWidth="500" d:DesignHeight="500">
    <Border>
        <TextBlock Text="content"></TextBlock>
        <!--插槽-->
        <ContentControl x:Name="contentSlot"></ContentControl>
    </Border>
</UserControl>
```

usercontrol.xaml.cs

```csharp
//将插槽暴露出去
public object InnerContent(){
    get{return contentSlot.Content;}
    set{contentSlot.Content = value;}
}
```



### ItemsControl

#### 颜色交替

VM

```xaml
using System.Collections.ObjectModel;
using System.Windows.Media;
using CommunityToolkit.Mvvm.ComponentModel;
using CommunityToolkit.Mvvm.Input;
using HZMAPP.Models;

namespace HZMAPP.ViewModels;

public partial class AppstorePageVM:ObservableObject
{
    public ObservableCollection<int> Lis { get; } = new() { 1,2,3,4};
}
```

xaml

```xaml
<ItemsControl
    AlternationCount="2"
    ItemsSource="{Binding Lis}">
    <ItemsControl.ItemTemplate>
        <DataTemplate>
            <Border>
                <Border.Style>
                    <Style TargetType="Border">
                        <Setter Property="Background" Value="Aqua"></Setter>
                        <Style.Triggers>
                            <DataTrigger
                                Binding="{Binding (ItemsControl.AlternationIndex),
                                RelativeSource={RelativeSource AncestorType=ContentPresenter}}"
                                Value="1">
                                <Setter Property="Background" Value="AntiqueWhite"></Setter>
                            </DataTrigger>
                        </Style.Triggers>
                    </Style>
                </Border.Style>
                <TextBlock Text="{Binding}"></TextBlock>
            </Border>
        </DataTemplate>
    </ItemsControl.ItemTemplate>
</ItemsControl>
```



### 滚动条样式

```xaml
<Page.Resources>
    <Style TargetType="ScrollBar">
        <Setter Property="Width" Value="4"></Setter>
        <Setter Property="Background" Value="Transparent"></Setter>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="ScrollBar">
                    <Grid
                        Width="8"
                        HorizontalAlignment="Right"
                        Background="AliceBlue">
                        <Track x:Name="PART_Track" IsDirectionReversed="True">
                            <Track.DecreaseRepeatButton>
                                <RepeatButton Command="ScrollBar.PageUpCommand" Opacity="0" Focusable="False"></RepeatButton>
                            </Track.DecreaseRepeatButton>
                            <Track.IncreaseRepeatButton>
                                <RepeatButton Command="ScrollBar.PageDownCommand" Opacity="0" Focusable="False"></RepeatButton>
                            </Track.IncreaseRepeatButton>
                            <Track.Thumb>
                                <Thumb>
                                    <Thumb.Template>
                                        <ControlTemplate TargetType="Thumb">
                                            <Border
                                                Background="Aquamarine"
                                                CornerRadius="6"
                                                ></Border>
                                        </ControlTemplate>
                                    </Thumb.Template>
                                </Thumb>
                            </Track.Thumb>
                        </Track>
                    </Grid>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
</Page.Resources>
```



### 动效制作

#### DoubleAnimation





#### ColorAnimation



#### ThicknessAnimation



#### DoubleAnimationUsingKeyFrames关键帧动画



## Style

### 阴影

| 属性          | 范围                  | 描述                    |
| ------------- | --------------------- | ----------------------- |
| BlurRadius    | 0 ~                   | 模糊半径                |
| ShadowDepth   | 0 ~                   | 阴影偏移距离，0为正下方 |
| Direction     | 0 ~ 360               | 阴影方向角度            |
| Opacity       | 0 ~ 1                 | 不透明度                |
| Color         | 任意颜色              | 颜色                    |
| RenderingBias | Performance / Quality | 渲染偏向                |



**eg**：

```xaml
<Border>
	<Border.Effect>
        <DropShadowEffect
            Color="#939393"
            BlurRadius="20"
            ShadowDepth="0"
            Direction="0"></DropShadowEffect>
    </Border.Effect>
</Border>
```



### 颜色渐变

