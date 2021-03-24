# Formatting text
You've probably been linked here from one of my plugins. This page will show you how you can format text with RGB and create gradients. 

The syntax is very similar to that of the popular core plugin CMI.

### Using hex codes
To specify a single hex colour, type it out like this:

	{#ff00ff}This text will be bright pink!
It behaves in the same way as vanilla format codes.

### Gradients
This is where the real fun starts! LucyCommonLib, and by extension all my plugins, support two types of gradient:
#### RGB
RGB is is your "standard gradient". You give it two hex codes, it fades between them.

	{#ff0000>}this text will start as red but fade into yellow!{#ffff00<}
You can also specify extra formatting tokens to make the gradient bold, italic, etc. These are the same letters as you'd use in vanilla:

	{#ff00ff:lo>}this is the same but bold ('l') and italic (o)!{#ffff00<}

#### HSV
HSV (not to be confused with HSL) is where things start to get exciting. Instead of fading between red, green and blue, this type fades between two hues, keeping the saturation and value consistent. This creates a nice, uniform look if set up right. It's a little more complicated than RGB.

	{hsv:00aaff>}this text will be a nice pastel rainbow, isn't that cool?{ff<}

Let's break this down.
First of all, what does `00aaff` mean? It helps to have an understanding of how hexadecimal works for this part. Each value here is a two-digit hexadecimal number, in the range of (decimal) 0-255.

- 00 - the hue to start at
- aa - the saturation of the gradient
- ff - the value of the gradient

The number in the closing tag is the hue to finish at. So overall, the above example means "fade this text from hue 00 (zero) to FF (255), keeping a saturation of AA (170) and a value of FF (255).

As with RGB, you can specify extra formatters:

	{hsl:00aaff:lo>}the same nice pastel rainbow, but bold and italic!{ff<}

### Setting a plugin's accent colour
All my plugins have a setting for an "accent colour". You can use these codes here too, it just requires a special symbol!
For hex colours, you don't need to do anything special. If you want bright pink:

	accent: '{#ff00ff}'
is all you need.
Gradients are a little bit different but overall very simple - all you need to do is replace where the gradient text would normally go with "%s". For example, the default for most of my plugins is:

	accent:  '{#fa9efa>}%s{#9dacfa<}'

I do appreciate this is kinda complicated. If you'd like some help with it, feel free to join my support Discord server at https://support.lucyy.me. I'd love to help you!
