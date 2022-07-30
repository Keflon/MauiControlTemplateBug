# MauiControlTemplateBug
## Bug number [#9088](https://github.com/dotnet/maui/issues/9088)

Replacing a `ControlTemplate` on a custom-control using a `Style` fails to apply the `ControlTemplate`.  

The extracts below are taken from [MainPage.xaml](https://github.com/Keflon/MauiControlTemplateBug/blob/master/MauiControlTemplateBug/MainPage.xaml)  
The `test:TestControl` is found in the [Controls folder](https://github.com/Keflon/MauiControlTemplateBug/tree/master/MauiControlTemplateBug/Controls)  

## Replacing the ControlTemplate on a RadioButton works as expected ...
```xml
<ControlTemplate x:Key="AlternateRadioButtonControlTemplate">
    <VerticalStackLayout>
        <Label Text="RadioButton ControlTemplate replaced in MainPage.xaml by a Style"/>
        <ContentPresenter Content="{TemplateBinding Content}"/>
    </VerticalStackLayout>
</ControlTemplate>

<Style TargetType="RadioButton">
    <Setter Property="ControlTemplate" Value="{StaticResource AlternateRadioButtonControlTemplate}" />
</Style >
```

## Replacing the ControlTemplate on a custom-control does nothing ...
```xml
<ControlTemplate x:Key="AlternateTestControlTemplate">
    <VerticalStackLayout>
        <Label Text="This label is defined in MainPage.xaml in the ControlTemplate"/>
        <ContentPresenter Content="{TemplateBinding Content}"/>
    </VerticalStackLayout>
</ControlTemplate>

<Style TargetType="test:TestControl">
    <Setter Property="ControlTemplate" Value="{StaticResource AlternateTestControlTemplate}" />
</Style >
```

