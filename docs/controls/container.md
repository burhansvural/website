---
title: Container
sidebar_label: Container
---

Container allows to decorate a control with background color and border and position it with padding, margin and alignment. 

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

[Live example](https://flet-controls-gallery.fly.dev/layout/container)

### Clickable container

<img src="/img/docs/controls/container/clickable-container.gif" className="screenshot-50" />

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):
    page.title = "Containers - clickable and not"
    page.vertical_alignment = ft.MainAxisAlignment.CENTER
    page.horizontal_alignment = ft.CrossAxisAlignment.CENTER

    page.add(
        ft.Row(
            [
                ft.Container(
                    content=ft.Text("Non clickable"),
                    margin=10,
                    padding=10,
                    alignment=ft.alignment.center,
                    bgcolor=ft.colors.AMBER,
                    width=150,
                    height=150,
                    border_radius=10,
                ),
                ft.Container(
                    content=ft.Text("Clickable without Ink"),
                    margin=10,
                    padding=10,
                    alignment=ft.alignment.center,
                    bgcolor=ft.colors.GREEN_200,
                    width=150,
                    height=150,
                    border_radius=10,
                    on_click=lambda e: print("Clickable without Ink clicked!"),
                ),
                ft.Container(
                    content=ft.Text("Clickable with Ink"),
                    margin=10,
                    padding=10,
                    alignment=ft.alignment.center,
                    bgcolor=ft.colors.CYAN_200,
                    width=150,
                    height=150,
                    border_radius=10,
                    ink=True,
                    on_click=lambda e: print("Clickable with Ink clicked!"),
                ),
                ft.Container(
                    content=ft.Text("Clickable transparent with Ink"),
                    margin=10,
                    padding=10,
                    alignment=ft.alignment.center,
                    width=150,
                    height=150,
                    border_radius=10,
                    ink=True,
                    on_click=lambda e: print("Clickable transparent with Ink clicked!"),
                ),
            ],
            alignment=ft.MainAxisAlignment.CENTER,
        ),
    )

ft.app(main)
```
  </TabItem>
</Tabs>

### Container Image and Blend Mode Explained

#### What is blend modes?

We categorize blending modes into five sections based on their main outcome: Darker, Lighter, Contrast, Color, and Comparative.

##### Darker
Blend modes under Darker will help you amplify dark colors in your designs. Here’s a quick run-through of the options available to you:

**Darken:** keeps the darkest colors between the blend and base layers.
**Multiply:** keeps only the darker colors of the blend layer and makes light colors less opaque. The resulting color is always darker, except for where it’s pure white.
**Color Burn:** uses the colors from the blend layer to darken the base layer and increases the contrast between the two. Blending with white produces no change.
**Plus Darker:** works like Darken but with a stronger impact on mid-tones.
Darker blend modes are great for working with shadows or dark base layers. You can use them to create a more realistic and dynamic shadow effect or to add depth and texture to an image.

##### Lighter
Blend modes under Lighter will help you amplify light colors in your designs. Let’s take a look at the blend modes in this section.

**Lighten:** keeps the lightest colors between the blend and base layers. It’ll only lighten if the top layer is lighter than the brightness or luminance of the bottom layer.
**Screen:** keeps only the white and lighter colors of the blend layer and makes black or dark colors less opaque. In other words, it multiplies the inverse of the base and blend colors, giving a lighter result except for where it’s pure black.
**Color Dodge:** uses the colors from the blend layer to lighten the base layer, reducing the contrast between the two. Blending with black won’t produce any change.
**Plus Lighter:** works like Lighten but with a stronger impact on mid-tones.
Lighter blend modes are great for creating a shining effect or increasing the brightness of an image.

##### Contrast
Blend modes under Contrast are all about having the base and blend layers play off of each other. Here are the blend modes you can find in this section:

**Overlay:** works like Multiply if the base layer is darker or like Screen if it’s lighter.
**Hard Light:** combines Multiply and Screen using the brightness values of the top layer to make its calculations, whereas Overlay uses the base layer.
**Soft Light:** Similar to Overlay, it applies either a darkening or lightening effect based on the luminance values, but more subtle, without the harsh contrast.
Contrast blend modes are great for adding depth and dynamism to your images. For example, you can combine them with a Gaussian blur and use them to add a soft glow to a portrait photograph. 

##### Comparative
Blend modes under Comparative basically invert white or light colors. Here’s a quick run-through of the blend modes in this section:

**Difference:** subtracts the blend color from the base or vice versa, depending on which is brighter. When two pixels are the same, the result will be black.
**Exclusion:** behaves much the same way as Difference, but with less contrast between the layers because it doesn’t invert mid-tones.
Comparative blend modes are useful for creating subtle layered effects or inverting colors. You can also use them to test the difference between colors — if you’re into the scientific side of design.

##### Color
Blend modes under Color play with hues, saturation and brightness to help bring your designs to life. Here’s an overview of the blend modes in this section:

**Hue:** uses the blend layer’s hue while preserving the saturation and brightness of the base layer.
**Saturation:** uses the blend layer’s levels of saturation but keeps the hue and brightness of the base layer.
**Color:** uses the blend layer’s hue and saturation while preserving the brightness of the base layers.
**Luminosity:** uses the base layer’s brightness while preserving the hue and saturation of the base layer, creating the inverse effect of Color.
Color blend modes are great for photo editing. For example, you can use it to add warmth to a cool-toned photo or to create a retro look by desaturating the colors.

---


![Ekran görüntüsü_2024-09-23_12-14-31](https://github.com/user-attachments/assets/5ce60993-1ccc-4732-a0a7-8fe1cc152510)

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>
    ```python
    import flet as ft


def main(page: ft.Page):
    page.title="Using Blend Mode Demo"

    def dd1_changed(e):
        cnt2.image.color_filter.blend_mode=e.control.value
        cnt2.update()

    dd1=ft.Dropdown(
        width=250,
        label="Select blend mode",
        autofocus=True,
        on_change=dd1_changed,
        options=[
            ft.dropdown.Option("clear"),
            ft.dropdown.Option("color"),
            ft.dropdown.Option("colorBurn"),
            ft.dropdown.Option("colorDodge"),
            ft.dropdown.Option("difference"),
            ft.dropdown.Option("dst"),
            ft.dropdown.Option("dstATop"),
            ft.dropdown.Option("dstIn"),
            ft.dropdown.Option("dstOut"),
            ft.dropdown.Option("dstOver"),
            ft.dropdown.Option("exclusion"),
            ft.dropdown.Option("hardLight"),
            ft.dropdown.Option("hue"),
            ft.dropdown.Option("lighten"),
            ft.dropdown.Option("luminosity"),
            ft.dropdown.Option("multiply"),
            ft.dropdown.Option("overlay"),
            ft.dropdown.Option("plus"),
            ft.dropdown.Option("saturation"),
            ft.dropdown.Option("softLight"),
            ft.dropdown.Option("src"),
            ft.dropdown.Option("srcATop"),
            ft.dropdown.Option("srcIn"),
            ft.dropdown.Option("srcOut"),
            ft.dropdown.Option("srcOver"),
            ft.dropdown.Option("values"),
            ft.dropdown.Option("xor"),
        ]
    )

    cnt1 = ft.Container(
        width=300,
        height=300,
        bgcolor=ft.colors.ORANGE,
        image=ft.DecorationImage(
            src=f"https://picsum.photos/200/200?15"
        )
    )

    cnt2 = ft.Container(
        width=300,
        height=300,
        bgcolor=ft.colors.ORANGE,
        image=ft.DecorationImage(
            src=f"https://picsum.photos/200/200?15",
            color_filter=ft.ColorFilter(
                color=ft.colors.ORANGE,
                blend_mode=None
            ),
        ),

    )

    page.add(
        ft.Container(
            width=float("inf"),
            content=ft.Text(
                "BLEND MODE EXPLAINED",
                text_align=ft.TextAlign.CENTER,
                style=ft.TextStyle(size=26)
            ),
        ),
        ft.Divider(),
        ft.Row(controls=[
            ft.Text("Choose Blend Mode"),
            dd1
        ]),
        ft.Divider(),
        ft.Row(controls=[
            cnt1, cnt2
        ]))


ft.app(target=main)

    ```
  </TabItem>  
</Tabs>


## Properties

<img src="/img/docs/controls/container/container-diagram.png" className="screenshot-50" />

### `alignment`

Align the child control within the container.

Value is of type [`Alignment`](/docs/reference/types/alignment).

### `animate`

Enables container "implicit" animation that gradually changes its values over a period of time.

Value is of type [`AnimationValue`](/docs/reference/types/animationvalue).

### `bgcolor`

Defines the background [color](/docs/reference/colors) of the container.

### `blend_mode`

The blend mode applied to the `color` or `gradient` background of the container. 

Value is of type [`BlendMode`](/docs/reference/types/blendmode) and defaults to `BlendMode.MODULATE`.

### `blur`

Applies Gaussian blur effect under the container.

The value of this property could be one of the following:

* **a number** - specifies the same value for horizontal and vertical sigmas, e.g. `10`.
* **a tuple** - specifies separate values for horizontal and vertical sigmas, e.g. `(10, 1)`.
* **an instance of [`Blur`](/docs/reference/types/blur)**

For example:

```python
ft.Stack(
    [
        ft.Container(
            content=ft.Text("Hello"),
            image_src="https://picsum.photos/100/100",
            width=100,
            height=100,
        ),
        ft.Container(
            width=50,
            height=50,
            blur=10,
            bgcolor="#44CCCC00",
        ),
        ft.Container(
            width=50,
            height=50,
            left=10,
            top=60,
            blur=(0, 10),
        ),
        ft.Container(
            top=10,
            left=60,
            blur=ft.Blur(10, 0, ft.BlurTileMode.MIRROR),
            width=50,
            height=50,
            bgcolor="#44CCCCCC",
            border=ft.border.all(2, ft.colors.BLACK),
        ),
    ]
)
```

### `border`

A border to draw above the background color.

Value is of type [`Border`](/docs/reference/types/border).

### `border_radius`

If specified, the corners of the container are rounded by this radius.

Value is of type [`BorderRadius`](/docs/reference/types/borderradius).

### `clip_behavior`

The content will be clipped (or not) according to this option.

Value is of type [`ClipBehavior`](/docs/reference/types/clipbehavior) and defaults to `ClipBehavior.ANTI_ALIAS`
if `border_radius` is not `None`; otherwise `ClipBehavior.NONE`.

### `color_filter`

Applies a color filter to the container.

Value is of type [`ColorFilter`](/docs/reference/types/colorfilter).

### `content`

A child Control contained by the container.

### `decoration`

The background decoration.

Value is of type [`BoxDecoration`](/docs/reference/types/boxdecoration).

### `foreground_decoration`

The foreground decoration.

Value is of type [`BoxDecoration`](/docs/reference/types/boxdecoration).

### `gradient`

Defines the gradient background of the container.

Value is of type [`Gradient`](/docs/reference/types/gradient).

### `ignore_interactions`

Whether to ignore all interactions with this container and its descendants.

Defaults to `False`.

### `image`

An image to paint above the `bgcolor` or `gradient`. If `shape=BoxShape.CIRCLE` then this image is clipped to the circle's boundary; if `border_radius` is not `None`then the image is clipped to the given radii.

Value is of type [`DecorationImage`](/docs/reference/types/decorationimage).

### ~~`image_fit`~~

How to inscribe the image into the space allocated during layout. 

Value is of type [`ImageFit`](/docs/reference/types/imagefit) and defaults to `ImageFit.NONE`.

**Deprecated in v0.24.0 and will be removed in v0.27.0. Use [`image.fit`](#image) instead.**

### ~~`image_opacity`~~

Sets image opacity when blending with a background.

Value ranges between `0.0`(fully transparent) and `1.0`(fully opaque).

**Deprecated in v0.24.0 and will be removed in v0.27.0. Use [`image.opacity`](#image) instead.**

### ~~`image_repeat`~~

How to paint any portions of the layout bounds not covered by the image.

Value is of type [`ImageRepeat`](/docs/reference/types/imagerepeat) and defaults to `ImageRepeat.NO_REPEAT`.

**Deprecated in v0.24.0 and will be removed in v0.27.0. Use [`image.repeat`](#image) instead.**

### ~~`image_src`~~

Sets an image as a container background. See [`Image.src`](/docs/controls/image#src) for more details.

**Deprecated in v0.24.0 and will be removed in v0.27.0. Use [`image.src`](#image) instead.**

### ~~`image_src_base64`~~

Sets an image encoded as Base-64 string as a container background. See [`Image.src_base64`](/docs/controls/image#src_base64) for more details.

**Deprecated in v0.24.0 and will be removed in v0.27.0. Use [`image.src_base64`](#image) instead.**

### `ink`

`True` to produce ink ripples effect when user clicks the container.

Defaults to `False`.

### `ink_color`

The splash [color](/docs/reference/colors) of the ink response.

### `margin`

Empty space to surround the decoration and child control.

Value is of type [`Margin`](/docs/reference/types/margin) class or a number.

### `padding`

Empty space to inscribe inside a container decoration (background, border). The child control is placed inside this padding.

Value is of type [`Padding`](/docs/reference/types/padding) or a number.

### `rtl`

`True` to set text direction to right-to-left.

Defaults to `False`.

### `shadow`

Shadows cast by the container.

Value is of type [`BoxShadow`](/docs/reference/types/boxshadow) or a `List[BoxShadow]`.

### `shape`

Sets the shape of the container.

Value is of type [`BoxShape`](/docs/reference/types/boxshape) and defaults to `BoxShape.RECTANGLE`.

### `theme_mode`

Setting `theme_mode` "resets" parent theme and creates a new, unique scheme for all controls inside the container. Otherwise the styles defined in container's `theme` property override corresponding styles from the parent, inherited theme.

Value is of type [`ThemeMode`](/docs/reference/types/thememode) and defaults to `ThemeMode.SYSTEM`.

### `theme`

Allows setting a nested `theme` for all controls inside the container and down the tree.

Value is of type [`Theme`](/docs/cookbook/theming) class.

**Usage example**

```python
import flet as ft

def main(page: ft.Page):
    # Yellow page theme with SYSTEM (default) mode
    page.theme = ft.Theme(
        color_scheme_seed=ft.colors.YELLOW,
    )

    page.add(
        # Page theme
        ft.Container(
            content=ft.ElevatedButton("Page theme button"),
            bgcolor=ft.colors.SURFACE_VARIANT,
            padding=20,
            width=300,
        ),

        # Inherited theme with primary color overridden
        ft.Container(
            theme=ft.Theme(color_scheme=ft.ColorScheme(primary=ft.colors.PINK)),
            content=ft.ElevatedButton("Inherited theme button"),
            bgcolor=ft.colors.SURFACE_VARIANT,
            padding=20,
            width=300,
        ),
        
        # Unique always DARK theme
        ft.Container(
            theme=ft.Theme(color_scheme_seed=ft.colors.INDIGO),
            theme_mode=ft.ThemeMode.DARK,
            content=ft.ElevatedButton("Unique theme button"),
            bgcolor=ft.colors.SURFACE_VARIANT,
            padding=20,
            width=300,
        ),
    )

ft.app(main)
```

<img src="/img/blog/theme-scrolling/nested-themes.png"  className="screenshot-60" />

### `url`

The URL to open when the container is clicked. If provided, `on_click` event is fired after that.

### `url_target`

Where to open URL in the web mode.

Value is of type [`UrlTarget`](/docs/reference/types/urltarget) and defaults to `UrlTarget.BLANK`.

## Events

### `on_click`

Fires when a user clicks the container. Will not be fired on long press.

### `on_hover`

Fires when a mouse pointer enters or exists the container area. `data` property of event object contains `true` (string) when cursor enters and `false` when it exits.

A simple example of a container changing its background color on mouse hover:

```python
import flet as ft

def main(page: ft.Page):
    def on_hover(e):
        e.control.bgcolor = "blue" if e.data == "true" else "red"
        e.control.update()

    page.add(
        ft.Container(width=100, height=100, bgcolor="red", ink=False, on_hover=on_hover)
    )

ft.app(main)
```

### `on_long_press`

Fires when the container is long-pressed.

### `on_tap_down`

Fires when a user clicks the container with or without a long press.

Event handler argument is of type [`ContainerTapEvent`](/docs/reference/types/containertapevent).

:::info
If `ink` is `True`, `e` will be plain `ControlEvent` with empty `data` instead of `ContainerTapEvent`.
:::

A simple usage example:

```python
import flet as ft

def main(page: ft.Page):
    page.vertical_alignment = ft.MainAxisAlignment.CENTER
    page.horizontal_alignment = ft.CrossAxisAlignment.CENTER

    def on_long_press(e):
        print("on long press")
        page.add(ft.Text("on_long_press triggered"))

    def on_click(e):
        print("on click")
        page.add(ft.Text("on_click triggered"))

    def on_tap_down(e: ft.ContainerTapEvent):
        print("on tap down", e.local_x, e.local_y)
        page.add(ft.Text("on_tap_down triggered"))

    c = ft.Container(
        bgcolor=ft.colors.RED,
        content=ft.Text("Test Long Press"),
        height=100,
        width=100,
        on_click=on_click,
        on_long_press=on_long_press,
        on_tap_down=on_tap_down,
    )
    
    page.add(c)

ft.app(main)
```
