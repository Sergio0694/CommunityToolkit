---
title: DateTimeOffsetConverter - .NET MAUI Community Toolkit
author: cliffagius
description: "The DateTimeOffsetConverter is a converter that allows users to convert a DateTimeOffset to a DateTime "
ms.date: 03/22/2022
---

# DateTimeOffsetConverter

[!INCLUDE [docs under construction](../includes/preview-note.md)]

The `DateTimeOffsetConverter` is a converter that allows users to convert a `DateTimeOffset` to a `DateTime`. Sometimes a `DateTime` value is stored with the offset on a backend to allow for storing the timezone in which a `DateTime` originated from. Controls like the `Microsoft.Maui.Controls.DatePicker` only work with `DateTime`. This converter can be used in those scenarios.

## Syntax

### XAML

The `DateTimeOffsetConverter` can be used as follows in XAML:

```xaml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:toolkit="http://schemas.microsoft.com/dotnet/2022/maui/toolkit"
             x:Class="MyLittleApp.MainPage">
    <ContentPage.Resources>
         <ResourceDictionary>
             <toolkit:DateTimeOffsetConverter x:Key="DateTimeOffsetConverter" />
         </ResourceDictionary>
    </ContentPage.Resources>

    <VerticalStackLayout>
            <Label Text="The DatePicker below is bound to a Property of type DateTimeOffset."
                   Margin="16"
                   HorizontalOptions="Center"
                   FontAttributes="Bold" />

            <DatePicker Date="{Binding TheDate, Converter={StaticResource DateTimeOffsetConverter}}" 
                   Margin="16"
                   HorizontalOptions="Center" />

            <Label Text="{Binding TheDate}"
                   Margin="16"
                   HorizontalOptions="Center"
                   FontAttributes="Bold" />
        </VerticalStackLayout>
</ContentPage>
```



### C#

The `DateTimeOffsetConverter` can be used as follows in C#:

```csharp
class DateTimeOffsetConverterPage : ContentPage
{
    public DateTimeOffsetConverterPage()
    {
        var label = new Label();

		label.SetBinding(
			Label.TextProperty,
			new Binding(
				nameof(ViewModels.MyValue),
				converter: new DateTimeOffsetConverter()));

		Content = label;
    }
}
```

### C# Markup

Our [`CommunityToolkit.Maui.Markup`](../markup/markup.md) package provides a much more concise way to use this converter in C#.

```csharp
using CommunityToolkit.Maui.Markup;

class DateTimeOffsetConverterPage : ContentPage
{
    public DateTimeOffsetConverterPage()
    {
        Content = new Label()
            .Bind(
                Label.TextProperty,
                nameof(ViewModel.MyValue),
                converter: new DateTimeOffsetConverterPage());
    }
}
```

## Examples

You can find an example of this converter in action in the [.NET MAUI Community Toolkit Sample Application](https://github.com/CommunityToolkit/Maui/blob/main/samples/CommunityToolkit.Maui.Sample/Pages/Converters/DateTimeOffsetConverterPage.xaml).

## API

You can find the source code for `DateTimeOffsetConverter` over on the [.NET MAUI Community Toolkit GitHub repository](https://github.com/CommunityToolkit/Maui/blob/main/src/CommunityToolkit.Maui/Converters/DateTimeOffsetConverter.shared.cs).
