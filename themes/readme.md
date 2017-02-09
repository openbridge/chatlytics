# Chatlytics Themes 
Chatlytics data visualizations have customizable components: the color palette and typography. Users may create their own themes to use when generating charts. When creating a theme, aesthetics should be considered, but more important is the legibility of the data visualization, which allows for better user engagement.

We include three amazing themes as a default, but you may want to create your own. We support that! The process is simple and if you follow best practices for the use of color and typography, you can create some highly customized and effective visualizations.

## Here's whats coming up: 
##### 1. We'll go through the 3 premade Chatlytics themes and the thought process behind creating them
##### 2. Best practices for your customization
##### 3. Guide for implementation of your custom styles
##### 4. Usage in messenger

<hr>
## (1) Existing Themes
We followed ideas from Samantha Zhang's research of color in data visualization in this [article] (https://blog.graphiq.com/finding-the-right-color-palettes-for-data-visualizations-fcd4e707a283#.sawb2zvkw).

3 beautiful themes are already included in Chatlytics: Blue, Sunrise, and Spring. All of these themes were creating following Zhang's advice to use colors inspired by nature. 

#### Blue is a commonly loved color so we chose that for a monochromatic palette.

| Nature Image  | Palette       |
| ------------- |:-------------:| 
| <img src="https://s3.amazonaws.com/ob-dataviz/blueinspiration" align="left" width="150" > | <img src="https://s3.amazonaws.com/ob-dataviz/blueline.png" align="left" width="650" >   |


#### Sunset was created to satsify something with a little more hue variety and a more sophistacted/formal look because of its dark colors.  
| Nature Image  | Palette       |
| ------------- |:-------------:| 
| <img src="https://s3.amazonaws.com/ob-dataviz/sunsetinspiration" align="left" height="80" > | <img src="https://s3.amazonaws.com/ob-dataviz/sunsetdonut.png" align="left" width="530" >   |

#### Lastly, Spring is more varied and a brighter more fun palette.   
| Nature Image  | Palette       |
| ------------- |:-------------:| 
| <img src="https://s3.amazonaws.com/ob-dataviz/springinspiration" align="left" height="300" > | <img src="https://s3.amazonaws.com/ob-dataviz/springbox.png" align="left" width="450" >   |


## (2) Customization Best Practices
### Step One: Designing a Theme - Understanding Color & Typography
As we mentioned earlier you need to think about color and typography. Both are critical to creating visualizations that tell stories with your data. 
### COLOR
For example, for a color palette, it's important to consider how many colors will be used, and to make sure each color is different enough from the others in the palette so that the eye can quickly separate different data representations.

To accomplish this, it's recommended to use colors that vary in hue and brightness slightly. See [this article] (https://blog.graphiq.com/finding-the-right-color-palettes-for-data-visualizations-fcd4e707a283#.sawb2zvkw) by Samantha Zhang.

Notice the varying HSV values in the existing color palettes; H representing Hue, S representing saturation, and V brightness. 

#### Sunset
![Alt text](https://s3.amazonaws.com/ob-dataviz/palette1 "Optional title")
#### Spring
![Alt text](https://s3.amazonaws.com/ob-dataviz/palette2 "Optional title")
#### Blue
![Alt text](https://s3.amazonaws.com/ob-dataviz/palette3 "Optional title")

  

### Color blindness  
**:warning: With any color palette for data visualization it's important to be cognizant of color blindness.**

You should test for how your colors look in all types of color blindless lenses, but the most common type of color blindness is Deuteranomaly. For a person with no color-blindness, this is what the palettes look like for someone with Deuteranomaly:
![Alt text](https://s3.amazonaws.com/ob-dataviz/colorblindpalette "Optional title")


There are generally 2 types of color palettes: Monochromatic // non
If creating an all one color palette, start with one base color - either a mid-tone or darkest tone is usually the best - and increase/decrease the hue and brightness accordingly.

For larger data sets it makes sense to use a wider variety of hues, using some variation of each. For example:



#### Color selection tools:
- We used www.coolors.co to create 5 color palettes

#### Inspiration palettes: 
- http://www.lolcolors.com/
- http://www.colorhunt.co/c/39609

#### Color contrast checker
- http://colorsafe.co/

<hr>
### TYPOGRAPHY
You can easily import any font-family into your css stylesheet. The most important thing with type is legibility. This means a reasonable font size so users can easily reference the legend and understand what the graph means. In addition, the typography in data visualization should not use any display fonts-- this will be harder to read and distracting from the main purpose-- the visualization. 

https://richardbrath.wordpress.com/2015/11/30/font-legibility-and-data-visualization/

** Our default: Open Sans.  **
Recommended Google fonts: 

Sans Serif:
- Lato
- Libre Franklin

Serif:
- Slabo
- Merriweather
- Droid Serif.

An easy bet that your font will be legible is to use a monospaced type: 
Typewolf recommends these: https://www.typewolf.com/top-10-monospaced-fonts


## (3) Implementation
### Step 1: Naming & Setup
Themes should have short names, ideally 1 or 2 words. They need to be all lower-case and separated with dashes like "spring-time" or "fall-harvest".

You will need to set up a directory for your theme inside the base stylesheet inside * plugins > query > themes * 
If your theme name is "fall-harvest", create a directory inside "themes" named "fall-harvest", and inside insert a duplicate of the base stylesheet that you can find in "themes".

### Step 2: Customization 
Replace the strokes and fills for each color with the new hex color codes. Add as many colors as you'd like following the naming structure in place (.color-5, .color-6. color-7 and so on.)
```
.color-0 {
  stroke: #261e7f;
  fill: #261e7f;
}

.color-1 {
  stroke: #264aa5;
  fill: #264aa5;
}
.color-2 {
  stroke: #277ace;
  fill: #277ace;
}

.color-3 {
  stroke: #2bb3e5;
  fill: #2bb3e5;
}
.color-4 {
  stroke: #37d5fc;
  fill: #37d5fc;
}
```


## You've set up your theme! Now what?
## (4) Usage
To put your theme to use, you simply add the theme name you chose into your slack command.

For example: !line fall-harvest 


