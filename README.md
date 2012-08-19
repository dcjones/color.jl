

# Color

Color is a Julia packages that lends a sophisticated notion of color to anyone
who so desires one.  It supports sRGB, HSV, HLS, XYZ, LAB, LUV, LCHab, and LCHuv
colorspaces with the ability to convert arbitrarily between any of these, as
well as functions to white-balance (e.g., when you want your graphics to look
the same under florescent and incandescent light), and the full spectrum of
X11/W3C named colors ("Misty Rose 4" anyone?).


# Synopsis 

```julia
c = parse_color("Indian Red") # parse a named colors
c = convert(LCHuv, c)         # convert from RGB to a percutually uniform colorspace
c.h += 15.0                   # tweak the hue
c = convert(RGB, c)           # convert back to RGB
println(hex(c))               # print in hex notation (#C46536)
```


## Background

Whenever a range of colors is used to convey information, problems arise. Human
perception of color was shaped largely by the need for our hairier,
tree-dwelling ancestors to tell when fruit is ripe.  It is not equipped to
accurately determine elevation on a rainbow colored topological map. Colors
chosen on linear scales are perceived as anything but by our species' sorry
excuse for color-vision.

This issue is not new to artists. The first to tackle this problem in a
serious way was Albert Munsell, who developed his very own extra-special color
system that approximates human vision, first published in 1905. Scientists who
wanted to record colors of things (e.g. soil samples), compensating for our
ocular shortcomings, jumped on the Munsell bandwagon.  Fortunately for us, this
idea was thoroughly rescued from the humanities department, and rigor-ized
through careful empirical measurements combined with ad-hoc mathematical
modeling in the form of the International Commission on Illumination's (CIE,
after the actual, French name) LAB and LUV colorspaces.

Despite these standardizations existing since the '70s, almost every plotting
tool in existence still gets color disastrously wrong. One exception is R, which
was finally rescued from the catastrophe with Ross Ihaka's work on the
colorspace package, and ggplot2 now uses HCL (i.e., LUV with hue in polar
coordinates) colors by default. The goal of this package preempt the need to
rescue Julia from RGBland.



## References

What perceptually uniform colorspaces are and why you should be using them:

Ihaka, R. (2003) Colour for Presentation Graphics

Zeileis, A., Hornik, K., and Murrell, P. (2009). Escaping RGBland: Selecting colors for statistical graphics. Computational Statistics & Data Analysis, 53(9), 3259–3270. doi:10.1016/j.csda.2008.11.033


