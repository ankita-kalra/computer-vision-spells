## Canny Edge Detection 

Here we will learn about canny edge detection. There are 4 most important steps in it. Let's go through it one by one.

### Gaussian Noise Filtering

1. Filter out any noise. The Gaussian filter is used for this purpose. 

### Intensity Gradient

2. Find the intensity gradient of the image. Apply a pair of convolution masks in x and y directions. Consequently, we find the gradient strength by taking the combined L2 norm and calculate the direction by finding arctan in x and y direction. .
The direction is rounded to one of four possible angles (namely 0, 45, 90 or 135).

```
G_{x} = \begin{bmatrix}
-1 & 0 & +1  \\
-2 & 0 & +2  \\
-1 & 0 & +1
\end{bmatrix}

G_{y} = \begin{bmatrix}
-1 & -2 & -1  \\
0 & 0 & 0  \\
+1 & +2 & +1
\end{bmatrix}
```


```
\begin{array}{l}
G = \sqrt{ G_{x}^{2} + G_{y}^{2} } \\
\theta = \arctan(\dfrac{ G_{y} }{ G_{x} })
\end{array}
```

### Non-maximum suppression

3. This removes pixels that are not considered to be part of an edge. Hence, only thin lines (candidate edges) will remain.
### Hysteresis Thresholding
4. This is the final step in Canny Edge Detection. Here we use two thresholds, upper and lower
   a) If a pixel gradient is higher than the upper threshold, the pixel is accepted as an edge
   b) If a pixel gradient value is below the lower threshold, then it is rejected.
   c) If the pixel gradient is between the two thresholds, then it will be accepted only if it is connected to a pixel that is above the upper threshold. Sir John Canny recommended a upper:lower ratio between 2:1 and 3:1.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ankita-kalra/computer-vision-spells/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
