# Guidelines for typesetting documents


## Writing style

Writing a journal paper or a thesis is not an exercise in modern literature. Keep your writing style simple, clear and concise.

If in doubt about a particular idiom, use a trusted resource such as "Practical English Usage" by M. Swan. Google is not always your friend when it comes to grammar and spelling.

Use the present tense or past tense consistently and avoid mixing them. If you choose to write your paper in the present tense, use it throughout. It is only on rare occasions that a different tense from the rest of the document can be used.

Relying too heavily on the passive voice is very common. Try instead to use the active voice whenever possible.

## Equations

### Italic vs roman

A general guideline is that a variable is typeset in italic whereas constants or mathematical entities with well-known definitions should be typeset in roman fonts. For instance the following constants are typeset in roman:
* The imaginary unit i
* The imaginary unit j
* Euler's constant e
* The ordinary derivative symbol d, which is also used to denote the integration element.

As an example the definition of the Fourier transform can be typeset as follows
```latex
\hat{f}(\omega) = \int f(t) \mathrm{e}^{\mathrm{i}\omega t}\,\mathrm{d}t
```

This applies also to well known functions such as the cosine, sine, tangent functions for which specific macros are defined in LaTeX: `\cos`, `\sin` and `\tan`. Another example is the Bessel functions which should be typeset `\mathrm{J}_m`.

If a variable is used in a subscript or a superscript it should be typeset in italic. For instance the components of a vector a would be written:
```latex
a_i
```
where `i` is the variable index.

By contrast, if a subscript or superscript is not a variable, it should not be typeset in italic but in roman. For instance for the maximum pressure we can write:
```latex
p_\mathrm{max}
```


### Bold

Reserve the use of bold symbols for vectors and matrices.

For bold greek letters, you will have to use the `\boldsymbol` command instead of `\mathbf`.

A common mistake is to include subscripts into the `\mathbf` command. For instance if i is an index then instead of
```latex
\mathbf{A_i}
```
you should write
```latex
\mathbf{A}_i
```

### Parentheses

The order of precedence should be parentheses, square brackets and then curly braces:
```latex
\{ [ (x+a) +b ] +c \}
```


### Fractions

Except in displayed equations, avoid using `\frac` in inline equations. For instance instead of
```latex
The value is $d=\frac{h}{8}$.
```
you should prefer
```latex
The value is $d=h/8$.
```


### Scalar product

The scalar product is typeset using the `\cdot` command and should not be written using the period `.` character.


### Units

Units are typeset in roman fonts and separated by a thin space from the value. This can be implemented with the following command:
```latex
\newcommand{\unit}[1]{\,\mathrm{#1}}
```
Alternatively you can use the `units` package.


## Encoding

Use the Unicode encoding for your LaTeX files and place the following in the preamble:
```latex
\usepackage[utf8]{inputenc}
```


## Figures

As much as possible, export your figures from Matlab or Python as vector graphics, such as eps or pdf, instead of bitmap file formats such as png and jpg.

The default line width is too thin in both Matlab and Python. It is generally preferable to increase the line width and the font size to make the graph more legible, especially if it is used in slides for a presentation. For instance in Matlab you could use
```matlab
x = linspace(0, 10, 300);
f = cos(x);
plot(x, f);
set(gca, 'LineWidth', 1, 'FontSize', 13);
set(get(gca, 'Children'), 'LineWidth', 1.5);
```
In python you can adjust the default settings of `matplotlib` as follows:
```python
import numpy as np
import matplotlib as mpl
import matplotlib.pyplot as plt
mpl.rc('lines', linewidth=1.5)
mpl.rc('font', size=13)
mpl.rc('axes', linewidth=1, labelsize=13)
mpl.rc('legend', fontsize=13)

x = np.linspace(0, 10, 300);
f = np.cos(x);
plt.plot(x, f);
```
