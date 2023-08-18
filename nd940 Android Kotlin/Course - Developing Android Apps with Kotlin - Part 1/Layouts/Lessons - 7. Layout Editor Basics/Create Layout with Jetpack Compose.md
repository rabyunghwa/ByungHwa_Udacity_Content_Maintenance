# Jetpack Compose Basics

First, let's briefly walk through how to create a new Android project that supports Jetpack Compose in Android Studio.

1. From the Android Studio welcome screen, click **New Project** and then **Empty Activity**. If a project is already open, you can select **File** > **New** > **New Project** from the menu bar.
2. Type in your desired project and package names. We'll name our project "UdacityJetpackComposeLayoutEditorReplacement". The package name will be "com.example.udacityjetpackcomposelayouteditorreplacement".
3. Minimum API level should be set to **21** or higher as Compose doesn't support a lower API.
4. Click **Finish**.

![Screenshot_2023-08-17_11-39-14](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/d26af5a5-b122-4ce9-a990-5b9f1de46599)

> To learn about how to set up Compose for an existing XML layout project, you can check [this](https://developer.android.com/jetpack/compose/setup#setup-compose) out.

It's worth noting that as of [Android Studio Flamingo | 2022.2.1](https://androidstudio.googleblog.com/2023/04/android-studio-flamingo-now-available.html), the **Empty Activity** template will create a new empty Jetpack Compose project by default while the **Empty Views Activity** template will create a new project that uses XML layouts.

Once the newly created project is done loading, open **MainActivity.kt**:

![Screenshot_2023-08-18_14-46-51](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/e3ca52c0-fa8a-43ca-8c0d-8ca652603a34)

We'll see one major difference between a newly created Jetpack Compose project and an XML layout one: the absence of the **layout** resource folder.

![Screenshot_2023-08-17_12-12-22](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/228e1ba2-495d-4e3c-a4cf-8c14fa786ece)

Instead of using XML, we build compose layouts in Kotlin exclusively, using composable functions annotated with **@Composable**:

```
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text(
        text = "Hello $name!",
        modifier = modifier
    )
}
```

Composable functions, the building blocks of UI in Compose, are just regular Kotlin functions annotated with **@Composable**. The composable function above renders some [text](https://developer.android.com/jetpack/compose/text). It is the equivalent of the [TextView](https://developer.android.com/reference/kotlin/android/widget/TextView) UI widget defined in an XML layout. To see what other composable functions Compose provides, you can check [this](https://developer.android.com/reference/kotlin/androidx/compose/material/package-summary) out. 

We can [preview](https://developer.android.com/jetpack/compose/tooling/previews) composable layouts by using parameterless composable functions annotated with **@Preview**:

```
@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    UdacityJetpackComposeLayoutEditorReplacementTheme {
        Greeting("Android")
    }
}
```

**UdacityJetpackComposeLayoutEditorReplacementTheme** corresponds to the name of the theme defined in the **Theme.kt** file:

![Screenshot_2023-08-18_10-29-58](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/559ec54b-3322-4834-9214-212178a46f11)

For now, you don't need to know what a theme is. You'll learn about it later. Just rememer that if you copy and paste the code to your own project, the theme names should match.

If we select either **Split** or **Design** at the upper right corner:

![Screenshot_2023-08-17_16-25-42](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/750cf5ed-88d6-4f46-b0fc-7e3ecf9ae470)

we'll see the preview generated inside Android Studio:

![Screenshot_2023-08-17_16-28-09](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/2561fb0c-205b-4b82-b968-fc7033602701)

![Screenshot_2023-08-17_16-28-21](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/77c515a7-ab86-4573-9aa0-d19548d8473c)

As a practice, let's replace the text with an [icon](https://developer.android.com/jetpack/compose/graphics/images/material). Replace the **Greeting** composable function with the following one:

```
@Composable
fun IconExample(imageVector: ImageVector, modifier: Modifier = Modifier) {
    Icon(
        imageVector = imageVector,
        contentDescription = "Example Icon",
        modifier = modifier
    )
}
```

Then scroll up to **onCreate()**:

![Screenshot_2023-08-18_10-11-38](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/ff4340b5-b681-4bb3-b2d2-c35a1d2f922f)

, replace 

```
Greeting("Android")
```

with

```
                    IconExample(
                        imageVector = Icons.Default.Home
                    )
```

Let's add a preview composable function for it. Replace the **GreetingPreview** preview composable function with the following one:

```
@Preview(showBackground = true)
@Composable
fun IconExamplePreview() {
    UdacityJetpackComposeLayoutEditorReplacementTheme {
        IconExample(imageVector = Icons.Default.Home)
    }
}
```

We can see the rendered preview on the right hand side of Android Studio:

![Screenshot_2023-08-18_10-20-03](https://github.com/rabyunghwa/ByungHwa_Udacity_Content_Maintenance/assets/7411385/a3fb4700-8184-40e4-9e76-ebc9fc6387b9)

That's it for Jetpack Compose for now. You'll get used to it as you build more projects with this new UI framework.





