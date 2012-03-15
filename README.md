#MortGrid
##Super Simplified [LessCSS](http://lesscss.org/) Grid System

This grid system began before Twitter Bootstrap and is loosely based off of the [960 Grid System](http://960.gs)

I've recently modifed it to use lesscss namespacing.

###How it works
You specify the number of columns, the max width of your container, and the width of your gutter.
Column widths are automatically generated based on the above criteria.

###Why I still use it over Bootstrap's grid
Bootstrap has strict columns widths, and gutters.
I'm not a fan of having to think about how wide my columns should be in order for them to fit within a 960px container if I choose to have a 24 grid system.
Bootstrap's container is variable while the columns widths and gutters are static. This may work for others, not so much for me.

###Usage
Assuming 12 grid system
1. Import grid.less into your main less file

```
@import "grid";
```
2. Assign the grids container to your container element

```
#wrapper {
	#grid > .container();
}
```

3. Assign a block as a row or columns

```
section div.main {
	// .main is a new row
	#grid > .row();
	// it has a 2 children that create 2 columns
	div:first-child {
		#grid > .column(8);
	}
	div:last-child {
		#grid > .column(4);
	}
}
```
The above assigns `.main` as a new row, then its first child as an 8 column wide block and its last as a 4 column wide block.

###Other Options
__"push" or "offset"__ - This allows you to place your block to the right by __X__ number of columns 

```
#grid > .offset(3); // pushes the column to the right 3 columns
```

__"alpha", "omega" or both "alpha/omega"__ - This is a column param, it determines if the block should not have opening or closing (or neither) gutter padding. If it is not passed then it assume both padding

```
#grid > .column(3, 'alpha'); // removes the left padding of the column
#grid > .column(3, 'alpha/omega'); // removes the padding from both left and right sides of column
#grid > .column(6, 'omega'); // removes the padding from the right side of column
```

__"flush"__ - Similar to "alpha and omega". This option removes the padding of the assigned direction. Unlike "alpha" or "Omega" it doesn't modify the columns width.

```
#grid > .flush('right'); // shift the column to the right by the amount of the gutter
#grid > .flush('left'); // shifts the column to the left by the amount of the gutter
```

###Further configuration
- Number of columns: `@columnNum: 16`
- Gutter Width: `@gutterWidth` _spacing to left and right of column_
- Grid Container Width: `@containerWidth: 1020px` _column widths will be generated to fit within this_
