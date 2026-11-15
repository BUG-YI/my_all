# WinUI3

Winapp生成WinUI3项目

```cmd
winapp new --name MyWinUIApp --template winui --use-defaults
```



生成新的page页面

```bash
dotnet new winui-page -n 页面名 
```





建议结构

```
MyApp/                          ← 主项目（View 层）
├── Views/
│   ├── MainPage.xaml           ← 对应 Controller（界面）
│   └── MainPage.xaml.cs
├── ViewModels/
│   ├── MainViewModel.cs        ← 对应 Service（业务逻辑 + 状态）
│   └── SettingsViewModel.cs
├── Services/
│   ├── IUserService.cs         ← 业务逻辑
│   └── UserService.cs
├── Models/
│   ├── User.cs                 ← 数据模型
│   └── Order.cs
├── Repositories/
│   ├── IUserRepository.cs      ← 数据访问
│   └── UserRepository.cs
├── App.xaml
└── App.xaml.cs                 ← 启动引导（DI 注册）
```



## 1.  C#

### 窗口最小/最大大小

WindowsAppSDK 要求在1.7以上

```xaml
using Microsoft.UI.Windowing;
using WinRT;

if (AppWindow.Presenter.As<OverlappedPresenter>() is { } presenter)
{
    presenter.PreferredMinimumWidth = 550;
    presenter.PreferredMinimumHeight = 400;
}
```



### ContentDialog

```c#
var dialog = new ContentDialog
{
    Title = "打卡成功！",
    Content = readAllLines[r.Next(readAllLines.Length)],  //readAllLines字符数组，r随机生成数
    PrimaryButtonText = "NB",

    XamlRoot = this.Content.XamlRoot
};

dialog.Resources["ContentDialogBackground"] = new SolidColorBrush(Color.FromArgb(1,136 ,137 ,141));  //上板块背景色 
dialog.Resources["ContentDialogTopOverlay"] = new SolidColorBrush(Color.FromArgb(1,136 ,137 ,141));  //下板块背景色

btn.Content = "已打卡";

ContentDialogResult result = await dialog.ShowAsync();  //异步显示消息框
```



### 通知界面数据更改

```c#
//继承接口INotifyCollectionChanged
```







## 2.  XAML

### 2.1  命名空间

```xaml
xmlns:x="url"  <!--x是别名，后面在调用里面的东西时需要加上-->
```



### 2.2  控件

| 控件         | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| Button       | 按钮，响应用户输入                                           |
| Calendar     | 日历，允许用户使用可视化日历                                 |
| DatePicker   | 日历选择器，用户选择日期的控件                               |
| RadioButton  | 单选按钮                                                     |
| CheckBox     | 复选框，用户选择或取消                                       |
| ContextMenu  | 上下文菜单                                                   |
| DataGrid     | 数据网格，自定义网格显示数据                                 |
| Dialogs      | 对话框                                                       |
| GridView     | 网格视图，可以水平滚动的行和列显示项目集合                   |
| Image        | 图像                                                         |
| ListBox      | 列表框，用户可以选择的一系列项目内联列表的控件               |
| Menus        | 菜单，Windows菜单控件，可以分层组织与命令和事件处理程序关联的元素 |
| PasswordBox  | 密码框                                                       |
| Popup        | 弹窗，在应用程序窗口范围内显示内容                           |
| ProgressBar  | 进度条                                                       |
| ProgressRing | 进度环                                                       |
| RichEditBox  | 富文本框，包含格式化文本，链接，图像等                       |
| ScrollViewer | 滑动查看器，允许用户平移缩放内容                             |
| SearchBox    | 搜索框                                                       |
| Slider       | 滑块，允许用户沿轨道移动Thumb控件                            |
| TextBlock    | 文本块                                                       |
| TimePicker   | 时间选择器，允许用户设置时间                                 |
| ToggleButton | 切换按钮                                                     |
| ToolTip      | 工具提示，显示信息弹窗                                       |
| Window       | 窗口，提供最大/最小选项、标题栏、边框、和关闭 按钮的根窗口   |



### 2.3  布局

当应用程序在不同的屏幕分辨率上使用时，控件的固定像素排列不起作用。XAML 提供了一套丰富的内置布局面板来以适当的方式排列 GUI 元素。

| 面板        | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| StackPanel  | 是XAML中一个简单且有用的布局面板。在StackPanel中，子元素可以根据方向属性水平或垂直方式排列在单行中 |
| WrapPanel   | 子元素根据方向属性从左到右、上到下，按顺序排列               |
| DockPanel   | 定义一个区域，相对于彼此排列子元素，无论是水平还是垂直。可以使用Dock属性将元素停靠在上、下、左、右、中心 |
| CanvasPanel | 基础布局面板，其中子元素可以使用相对于Canvas任意一侧（上、下、左、右)的明确定位 |
| GridPanel   | 提供了一个灵活的区域，该区域由行和列组成。在Grid中，子元素可以以表格形式排列 |



### 2.4  事件处理

通常处理鼠标、键盘输入，如鼠标点击、长按、进入、离开等



以鼠标点击事件为例：

**MainWindow.xaml**

```xaml
<?xml version="1.0" encoding="utf-8" ?>
<Page
    x:Class="MyWinUIApp.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:local="using:MyWinUIApp"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    >
    
    <Grid Margin="15">
        <Button Click="ClickB" Content="click"/>
    </Grid>
</Page>

```

**MainWindow.xaml.cs**

```c#
public sealed partial class MainPage : Page
{

    public MainPage()
    {
        InitializeComponent();
        
    }

    //async异步
    private async void ClickB(object sender, RoutedEventArgs e)
    {
        var dialog = new ContentDialog
        {
            Title = "message",
            Content = "Button is clicked.",
            PrimaryButtonText = "primary",
            CloseButtonText = "cancel",
            //必要
            XamlRoot = this.Content.XamlRoot
        };

        ContentDialogResult result = await dialog.ShowAsync();

        if (result == ContentDialogResult.Primary)
        {
            Console.WriteLine("primary");
        }
        else
        {
            Console.WriteLine("cancel");
        }
    }
}
```



### 2.5  数据绑定

| 绑定模式        | 描述         |
| --------------- | ------------ |
| OneTime（默认） |              |
| OneWay          | 单向数据绑定 |
| TwoWay          | 双向数据绑定 |



#### 2.5.1  单向数据绑定

修改数据不回写，不更改源数据


```xaml
//key：绑定的数据变量
//OneWay：单向绑定模式
<TextBox Text="{x:Bind key, Mode=OneWay }"></TextBox>
```



例：

**MainPage.xaml**

```xaml
<Grid Margin="15">
    <StackPanel>
        <TextBox Height="20" Text="{x:Bind Person.Name, Mode=OneWay }"></TextBox>
        <Button Click="ClickB" Content="click"/>
    </StackPanel>
</Grid>
```

**MainPage.xaml.cs**

```c#
public sealed partial class MainPage : Page
{
    public Person Person {get;} = new Person("zhangs", 18);
    public MainPage()
    {
        InitializeComponent();
    }

    private async void ClickB(object sender, RoutedEventArgs e)
    {
        var dialog = new ContentDialog
        {
            Title = "message",
            Content = "Button is clicked.",
            PrimaryButtonText = "primary",
            CloseButtonText = "cancel",
            XamlRoot = this.Content.XamlRoot
        };

        ContentDialogResult result = await dialog.ShowAsync();

        if (result == ContentDialogResult.Primary)
        {
            Console.WriteLine("primary");
        }
        else
        {
            Console.WriteLine("cancel");
        }
    }
}

public class Person
{
    private string name;
    private int age;

    public Person(string name, int age)
    {
        this.age = age;
        this.name = name;
    }

    public int Age
    {
        get => age;
        set => age = value;
    }

    public string Name
    {
        get => name;
        set => name = value ?? throw new ArgumentNullException(nameof(value));
    }
}
```





#### 2.5.2  双向数据绑定

修改数据并回写，更改源数据

```xaml
//key：绑定的数据变量
//TwoWay：双向绑定模式
<TextBox Text="{x:Bind key, Mode=TwoWay }"></TextBox>
```

**MainPage.xaml**

Person的Name属性会更改

```xaml
<Grid Margin="15">
    <StackPanel>
        <TextBox Height="20" Text="{x:Bind Person.Name, Mode=TwoWay }"></TextBox>
        <Button Click="ClickB" Content="click"/>
    </StackPanel>
</Grid>
```



### 2.6  标记扩展

标记扩展是xaml中的`{}`标记的特殊语言，动态计算属性、值，不将数据写死

也可以通过继承 MarkupExtension 类并覆盖 ProvideValue 方法（MarkupExtension 类中的抽象方法）来定义自定义标记扩展。

类似于前端的CSS



**MainPage.xaml**

```xaml
<Page.Resources>
    <!--定义一个属性，便于后面使用-->
    <SolidColorBrush Color="Red" x:Key="Col"></SolidColorBrush>
</Page.Resources>

<Grid Margin="15">
    <StackPanel>
        <TextBox Height="20" Text="{x:Bind Person.Name, Mode=TwoWay }"></TextBox>
        <!--{StaticResource 属性}-->
        <Button Click="ClickB" Background="{StaticResource Col}" Content="click"/>
    </StackPanel>
</Grid>
```



### 2.7  依赖属性

ContentPresenter是ControlTemplate的内容占位符，内容可以是文本，图片，UIElement等

通过重写 ControlTemplate，实现内容颜色

```xaml
<Grid Margin="15">
    <StackPanel>
        <Button x:Name="myButton"
                Content="click" 
                Width="200" Height="100">
            <Button.Resources>
                <SolidColorBrush Color="Red" x:Key="RedC"></SolidColorBrush>
                <SolidColorBrush Color="Blue" x:Key="BlueC"></SolidColorBrush>
            </Button.Resources>
            
            <Button.Template>
                <ControlTemplate TargetType="Button">
                    <Grid Background="{TemplateBinding Background}">
                        <VisualStateManager.VisualStateGroups>
                            <VisualStateGroup x:Name="CommonStates">
                                <!--Normal，设置默认属性，不写的话默认颜色还是白色PointOver之后不会变成红色-->
                                <VisualState x:Name="Normal">
                                    <VisualState.Setters>
                                        <Setter Target="qw.Foreground" Value="{StaticResource RedC}"></Setter>
                                    </VisualState.Setters>
                                </VisualState>
                                <VisualState x:Name="PointerOver">
                                    <VisualState.Setters>
                                        <Setter Target="qw.Foreground" Value="{StaticResource BlueC}"></Setter>
                                    </VisualState.Setters>
                                </VisualState>
                            </VisualStateGroup>
                        </VisualStateManager.VisualStateGroups>
                        <ContentPresenter x:Name="qw"
                                          Content="{TemplateBinding Content}"
                                          Foreground="{TemplateBinding Foreground}"
                                          HorizontalAlignment="Center"
                                          VerticalAlignment="Center"/>
                    </Grid>
                </ControlTemplate>
            </Button.Template>
        </Button>
    </StackPanel>
</Grid>
```



### 2.8  资源

WinUI3没有window资源



#### 2.8.1  page资源

```xaml
<Page.Resources>
    <SolidColorBrush x:Key="ColorBrush" Color="Red"></SolidColorBrush>
</Page.Resources>
```



### 2.9  模板

#### 2.9.1 空间模板

**ControlTemplate**（控件模板）是改变控件的样式，使其模板与逻辑分离

**ContentPresenter**内容解析,是 **ControlTemplate** 里专门用来显示控件“内容”的元素——它把控件的 **Content** 渲染出来，是模板里内容显示的核心。**

```xaml
<Button x:Name="myButton"
        Content="click" 
        Width="200" Height="100">
    <Button.Resources>
        <SolidColorBrush Color="Red" x:Key="RedC"></SolidColorBrush>
        <SolidColorBrush Color="Blue" x:Key="BlueC"></SolidColorBrush>
    </Button.Resources>

    <Button.Template>
        <ControlTemplate TargetType="Button">
            <Grid Background="{TemplateBinding Background}">
                <VisualStateManager.VisualStateGroups>
                    <VisualStateGroup x:Name="CommonStates">
                        <VisualState x:Name="Normal">
                            <VisualState.Setters>
                                <Setter Target="qw.Foreground" Value="{StaticResource RedC}"></Setter>
                            </VisualState.Setters>
                        </VisualState>
                        <VisualState x:Name="PointerOver">
                            <VisualState.Setters>
                                <Setter Target="qw.Foreground" Value="{StaticResource BlueC}"></Setter>
                            </VisualState.Setters>
                        </VisualState>
                    </VisualStateGroup>
                </VisualStateManager.VisualStateGroups>
                <ContentPresenter x:Name="qw"
                                  Content="{TemplateBinding Content}"
                                  Foreground="{TemplateBinding Foreground}"
                                  HorizontalAlignment="Center"
                                  VerticalAlignment="Center"/>
            </Grid>
        </ControlTemplate>
    </Button.Template>
</Button>
```



#### 2.9.2  数据模板

**DataTemplate**（数据模板）定义“一个数据对象在界面上长什么样”，配合 `ListView`/`GridView` 等，把数据渲染成 UI。



**MainPage.xaml**

```xaml
<Grid Margin="15">
    <StackPanel>
      	<!--ItemsSource需要绑定一个数据列表-->
        <ListView ItemsSource="{x:Bind People}">
            <ListView.ItemTemplate>
                <!--x:DataType="local:类"-->
                <DataTemplate x:DataType="local:Person">
                    <StackPanel>
                        <!--类属性-->
                        <TextBlock Text="{x:Bind Name}"></TextBlock>
                    </StackPanel>
                </DataTemplate>
            </ListView.ItemTemplate>
        </ListView>
    </StackPanel>
</Grid>
```

**MainPage.xaml.cs**

```c#
public sealed partial class MainPage : Page
{
	//ObservableCollection 作用类似于List<T>
    public ObservableCollection<Person> People { get; } = new()
    {
        new Person("zhangs", 18),
        new Person("a", 10 )
    };
    public MainPage()
    {
        InitializeComponent();
    }
    
}

public class Person:INotifyPropertyChanged
{
    private string name;
    private int age;

    public Person(string name, int age)
    {
        this.age = age;
        this.name = name;
    }

    public int Age
    {
        get => age;
        set => age = value;
    }

    public string Name
    {
        get => name;
        set => name = value ?? throw new ArgumentNullException(nameof(value));
    }

    public event PropertyChangedEventHandler? PropertyChanged;
}
```

> [!tip]
>
> **ObservableCollection**<T>：是一个可通知UI变更的数据集合，ObservableCollection内容改变UI也会改变
>
> **List<T>**：数据发生更改UI不会改变



### 2.10  样式

显式样式

```xaml
<Style x:key="key值" TargetType="指定标签类型控件">
	<Setter Property="属性" Value="属性值"></Setter>
    ...
</Style>
```



隐式样式，没有设置`x:key`值，作用于所有设定的标签

```xaml
<Style TargetType="指定标签类型控件">
	<Setter Property="属性" Value="属性值"></Setter>
    ...
</Style>
```



例：

```xaml
<Page.Resources>
    <!--显式-->
    <Style x:Key="ButtonStyle" TargetType="Button">
        <Setter Property="Height" Value="50"></Setter>
        <Setter Property="Width" Value="100"></Setter>
        <Setter Property="Foreground" Value="Black"></Setter>
        <Setter Property="Background" Value="White"></Setter>
        <Setter Property="Grid.Row" Value="1"></Setter>
    </Style>
</Page.Resources>

<Grid Margin="15">
    <StackPanel>
        <!--使用样式-->
        <Button Style="{StaticResource ButtonStyle}" Content="click"></Button>
    </StackPanel>
</Grid>
```

> [!note]
>
> 隐式直接应用于所有被指定的类型控件，不用调用



#### 2.10.1  外观属性

| 属性            | 作用           |
| --------------- | -------------- |
| Background      | 背景           |
| Foreground      | 前景色（文字） |
| BorderBrush     | 边框颜色       |
| BorderThickness | 边框粗细       |
| CornerRadius    | 圆角           |
| Opacity         | 透明度         |
| Visibility      | 可见性         |



#### 2.10.2  布局

| 属性                | 作用        |
| ------------------- | ----------- |
| Width/Height        | 宽高        |
| Margin              | 外边距      |
| Padding             | 内边距      |
| HorizontalAlignment | 水平对齐    |
| VerticalAlignment   | 垂直对齐    |
| MinWidth/MaxWidth   | 最小/最大宽 |



#### 2.10.4  附加属性

| 属性                    | 作用       |
| ----------------------- | ---------- |
| Grid.Row                | Grid位置   |
| Grid.RowSpan/ColumnSpan | 跨行/列    |
| ToolTipService.ToolTip  | 悬停提示   |
| Canvas.Left/Canvas.Top  | Canvas位置 |



#### 2.10.3  字体属性

| 属性             | 作用   |
| ---------------- | ------ |
| FontSize         | 字号   |
| FontFamily       | 字体   |
| FontWeight       | 字重   |
| FontStyle        | 斜体   |
| CharacterSpacing | 字间距 |



#### 2.10.4  内容/数据

| 属性        | 数据           |
| ----------- | -------------- |
| Content     | 内容           |
| Text        | 文本           |
| ItemsSource | 数据源（列表） |



#### 2.10.5  行为

| 属性             | 作用         |
| ---------------- | ------------ |
| IsEnabled        | 是否可用     |
| IsHitTestVisible | 是否响应鼠标 |
| TabIndex         | tab顺序      |



**MainPage.xaml**

```xaml
<?xml version="1.0" encoding="utf-8" ?>
<Page
    x:Class="MyWinUIApp.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:local="using:MyWinUIApp"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    >
    <Page.Resources>
        <Style x:Key="ButtonStyle" TargetType="Button">
            <Setter Property="Height" Value="50"></Setter>
            <Setter Property="Width" Value="100"></Setter>
            <Setter Property="Background" Value="red"></Setter>
            <Setter Property="Foreground" Value="Black"></Setter>
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="Button">
                        <Grid Background="{TemplateBinding Background}">
                            <VisualStateManager.VisualStateGroups>
                                <VisualStateGroup x:Name="CommonStates">
                                    <VisualState x:Name="Normal">
                                        <VisualState.Setters>
                                            <Setter Target="cs.Foreground" Value="black"></Setter>
                                        </VisualState.Setters>
                                    </VisualState>
                                    <VisualState x:Name="PointerOver">
                                        <VisualState.Setters>
                                            <Setter Target="cs.Foreground" Value="white"/>
                                        </VisualState.Setters>
                                    </VisualState>
                                </VisualStateGroup>
                            </VisualStateManager.VisualStateGroups>
                            <ContentPresenter x:Name="cs"
                                              Content="{TemplateBinding Content}"
                                              Foreground="{TemplateBinding Foreground}"
                                              HorizontalAlignment="Center"
                                              VerticalAlignment="Center"></ContentPresenter>
                        </Grid>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
    </Page.Resources>
    
    <Grid Margin="15">
        <StackPanel>
            <Button Style="{StaticResource ButtonStyle}" Content="click"/>
        </StackPanel>
    </Grid>
</Page>
```



### 2.11  触发器

#### 2.11.1  AdaptiveTrigger（自适应触发器）













## 3  WinUI控件

### 3.1  侧边栏

MainPage.xaml

```xaml
<NavigationView x:Name="NavView"
                IsBackButtonVisible="Collapsed"
                IsSettingsVisible="False"
                PaneDisplayMode="LeftCompact"
                OpenPaneLength="120"
                Background="#240064"
                SelectionChanged="NavView_OnSelectionChanged">
    <NavigationView.MenuItems>
        <NavigationViewItem Content="首页" Tag="home">
            <NavigationViewItem.Icon><FontIcon Glyph="&#xE80F;"/></NavigationViewItem.Icon>
        </NavigationViewItem>
        <NavigationViewItem Content="设置" Tag="setting">
            <NavigationViewItem.Icon><FontIcon Glyph="&#xE713;"/></NavigationViewItem.Icon>
        </NavigationViewItem>
    </NavigationView.MenuItems>
    <Frame x:Name="ContentFrame"></Frame>
</NavigationView>
```

MainPage.xaml.cs

```c#
private void NavView_OnSelectionChanged(NavigationView sender, NavigationViewSelectionChangedEventArgs args)
{
    if (args.SelectedItem is NavigationViewItem item && item.Tag is string tag)
    {
        Type page = tag switch
        {
            "home" => typeof(HomePage),
            "setting" => typeof(SettingPage),
            _ => typeof(HomePage)
        };

        ContentFrame.Navigate(page);
    }
}
```





## MVVM



## Windows App SDK 和打包



