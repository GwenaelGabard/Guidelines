# Basic guidelines to write a scientific paper

## Writing style

Writing a journal paper or a thesis is not an exercise in modern literature. Keep your writing style simple, clear and concise.

If in doubt about a particular idiom, use a trusted resource such as "Practical English Usage" by M. Swan.
You should use a spell checker, such as [LanguageTool](https://languagetool.org/) which also checks for basic grammar mistakes (the free version is already very good).

Use the present tense or past tense consistently and avoid mixing them. If you choose to write your paper in the present tense, use it throughout. It is only on rare occasions that a different tense from the rest of the document can be used.

Many writers tend to rely too heavily on the passive voice. Try to use the active voice whenever possible.

The spelling of words can differ between British English and American English.
Make sure you use one of them consistently but don't mix them.
You should also configure your spell checker accordingly.

## Checklist

The following is a list of important things to check before submitting a paper to a journal (this list is taken from the Journal of Sound and Vibration but is probably applicable to many other journals):

- The manuscript has been 'spell checked' and 'grammar checked'.
- Journal policies have been reviewed.
- All authors are listed in the manuscript with correct affiliations, correct email address 
and are in correct order.
- One author has been designated as the corresponding author with contact details (e-mail address and full postal address).
- None of the figures of the manuscript has been already published in another journal.
- All figures, tables and equations are correctly numbered.
- All figures and tables have a caption.
- All figures and tables are cited at least once in the text of the manuscript.
- For multi-parts figures, each part is labelled, and the labels are defined in the figure caption.
- If two figures involving a colour map are meant to be compared, make sure that the extent of the colour bars is the same.
- All references mentioned in the reference list are cited in the text, and vice versa. 
- All abbreviations are defined (once only) the first time they appear in the text. If possible, abbreviations are avoided in the abstract. 
- All variables are defined (once only) the first time they appear in the text.
- Unit symbols should be upright (e.g. kg, not *kg*).
- Use Roman (normal upright) type for total differential operators (e.g. d in differential); i or j (square root of -1); exp or e (base of natural logarithms); Re or Im (real or imaginary part); log, ln, sin, cos, etc.; multiletter symbols (e.g. SPL for sound pressure levels)
- Figures in colour can be reproduced in black and white in the printed journal and must therefore be readable in both colour and black & white. Note that charges may apply for production of colour figures in the printed journal.
- The novelty of the paper has been clearly stated in the introduction.
- Acknowledgements should appear in a separate section just after the conclusions.
- In case material is reproduced from other publications (e.g. tables, figures), permission has been obtained for use of copyrighted material from other sources and source is acknowledged.


# Guidelines for typesetting documents using LaTeX

## Equations

### Italic vs Roman

A general guideline is that a variable is typeset in italic whereas constants or mathematical entities with well-known definitions should be typeset in Roman fonts. For instance the following constants are typeset in Roman:
* The imaginary unit i
* The imaginary unit j
* Euler's constant e
* The ordinary derivative symbol d, which is also used to denote the integration element.

As an example the definition of the Fourier transform can be typeset as follows
```latex
\hat{f}(\omega) = \int f(t) \mathrm{e}^{\mathrm{i}\omega t}\,\mathrm{d}t
```

This applies also to well-known functions such as the cosine, sine, tangent functions for which specific macros are defined in LaTeX: `\cos`, `\sin` and `\tan`. Another example is the Bessel functions which should be typeset `\mathrm{J}_m`.

If a variable is used in a subscript or a superscript it should be typeset in italic. For instance the components of a vector a would be written:
```latex
a_i
```
where $i$ is the variable index.

By contrast, if a subscript or superscript is not a variable, it should not be typeset in italic but in Roman. For instance for the maximum pressure we can write:
```latex
p_\mathrm{max}
```


### Bold

Reserve the use of bold symbols for vectors and matrices.

For bold Greek letters, you will have to use the `\boldsymbol` command instead of `\mathbf`.

A common mistake is to include subscripts into the `\mathbf` command. For instance if $i$ is an index then instead of
```latex
\mathbf{A_i}
```
you should write
```latex
\mathbf{A}_i
```

It is good practice to define two macros (for instance `\vec` and `\mat`) to typeset vectors and matrices in equations.
You can then easily change these definitions to adjust how vectors and matrices are shown throughout a document.


### Delimiters

The order of precedence should be parentheses, brackets and then braces:
```latex
\{ [ (x+a) +b ] +c \}
```

The mean value and a scalar product are sometimes denoted with angle brackets <>. Do not use the "smaller than" or "greater than" symbols, but use the proper LaTeX delimiters for this purpose:
```latex
\langle x \rangle
```

Remember to use the `\left` and `\right` commands to ensure the delimiters are scaled to the height of the mathematical expressions between these delimiters.
For instance, you should write
```latex
$$
\left( \int f(x)\,\mathrm{d}x \right)^2
$$
```
so as to get parentheses of the same size as the integral symbol:
$$
\left( \int f(x)\,\mathrm{d}x \right)^2 \; .
$$
If you omit the `\left` and `\right` macros, the parentheses are not scaled:
$$
( \int f(x)\,\mathrm{d}x )^2 \;.
$$


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


### Comparisons

To indicate that a quantity is much smaller (or much larger) than something else, use the LaTeX commands `\ll` and `\gg` to produce the symbols $\ll$ and $\gg$.
Do not use double inequality signs like `>>` or `<<`.


### Units

Units are typeset in Roman fonts and separated by a thin space from the value. This can be implemented with the following command:
```latex
\newcommand{\unit}[1]{\,\mathrm{#1}}
```
Alternatively you can use the `units` package.


### Punctuations

Both inline and displayed equations are parts of the sentences.
Punctuations should therefore be added around these equations.

If a displayed equation forms the last part of a sentence, you should add a period `.` at the end of the equation to indicate that this is also the end of the sentence.
For instance: 
```latex
We can then show that
$$
\cos(\pi) = -1 \; .
$$
```
Note that the period is separated from the equation by a thick space using the command `\;` (this is not mandatory but a common practice).

If a displayed equation is part of a longer sentence, it is generally ended by a comma `,`.
For instance
```latex
We define
$$
f(x) = a x \; ,
$$
where $a$ is a real constant.
```

## Encoding

Use the Unicode encoding for your LaTeX files and place the following in the preamble:
```latex
\usepackage[utf8]{inputenc}
```

## Hyphens and dashes

Hyphens (-) are used for phrasal adjectives such as
```latex
The right-hand side of the equation represents the quarter-wavelength resonator.
```

An en dash (–) is longer than a hyphen.
In LaTeX, it is written with a double hyphen `--`.
An en dash is typically used to create multipart words involving names.
For instance:
```latex
The Navier--Stokes equations and the Runge--Kutta schemes.
```
An en dash is also used for ranges of pages or dates.
For instance:
```latex
This is explained on pages 12--17.
```


## Figures

### File formats

As much as possible, export your figures from Matlab or Python as vector graphics, such as eps or pdf, instead of bitmap file formats such as png and jpg.

### Line and font sizes

The default line width is too thin in both Matlab and Python. It is generally preferable to increase the line width and the font size to make the graph more legible, especially if it is used in slides for a presentation. For instance in Matlab you could use
```matlab
x = linspace(0, 10, 300);
f = cos(x);
plot(x, f);
set(gca, 'LineWidth', 1, 'FontSize', 13);
set(get(gca, 'Children'), 'LineWidth', 1.5);
```
In Python you can adjust the default settings of `matplotlib` as follows:
```python
import numpy as np
import matplotlib as mpl
import matplotlib.pyplot as plt
mpl.rc('lines', linewidth=1.5)
mpl.rc('font', size=13)
mpl.rc('axes', linewidth=1, labelsize=13)
mpl.rc('legend', fontsize=13)

x = np.linspace(0, 10, 300)
f = np.cos(x)
plt.plot(x, f)
plt.show()
```


### Colour maps

Human eyes cannot distinguish colours accurately.
The choice of a colour map is therefore important.
The `jet` colour map used to be the default in Matlab and Python.
It is notoriously bad for colour-blind readers, and it is ambiguous when converted to grey scale.
Modern colour maps have been designed to be less ambiguous and more accessible to people with reduced colour vision.
See for instance the documentation of Matplotlib on [choosing colormaps](https://matplotlib.org/stable/tutorials/colors/colormaps.html).

In addition to colours, it is often useful to include contour lines to provide more precise visualisations and comparisons between graphs.


## Further reading

If you are curious to learn more about typography, the website [Practical Typography](https://practicaltypography.com/) is a good start.

Further reading on the use of colours in scientific communication:
* [Crameri, F., Shephard, G.E. & Heron, P.J. The misuse of colour in science communication. Nat Commun 11, 5444 (2020)](https://doi.org/10.1038/s41467-020-19160-7).
* [Scientific colour maps](https://www.fabiocrameri.ch/colourmaps/).
