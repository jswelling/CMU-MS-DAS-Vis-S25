## Thinking About Coordinates ##

To make the idea of a manifold more concrete, let's think about a real physical
object- Colin Holmes' head.



## Let's Use Colin's Brain

For this exercise, let's use the [Colin27 MRI Dataset](https://www.statnews.com/2017/08/02/colin-holmes-famous-brain-science/).  It's available in raw form [here](https://www.bic.mni.mcgill.ca/ServicesAtlases/Colin27).

A handy version, already converted to brick-of-bytes format, is on the
class web page in the data directory.


Assuming you've cloned the class Github repo, it's easy to get Colin27
in numpy form:
```
file_path = '/home/welling/git/CMU-MS-DAS-Vis-S25/data/colin27_icbm_181_217_181.bytes'
colin_tlrc = np.fromfile(file_path, dtype=np.uint8)
colin_tlrc = np.reshape(colin_tlrc, (181, 217, 181), order='F')
```
Obviously you need to customize file_path.

np.uint8 says that the data is in bytes.

The data dimensions are those of the [ICBM (International Consortium
for Brain Mapping) coordinate system](http://www.bmap.ucla.edu/portfolio/atlases/ICBM_Template/).  The byte order is (F)ortran,
meaning left-index-fastest.



## Generate Some 2D Contour Plots

We'll do this interactively in a Jupyterlab environment, but here are
the important bits.


It's easy to make a quick contour plot of the brain using matplotlib:
```
x = np.arange(0.0, colin_tlrc.shape[0], 1)
y = np.arange(0.0, colin_tlrc.shape[1], 1)
X, Y = np.meshgrid(x, y, indexing='ij')
fig, ax = plt.subplots()
countours = ax.contour(X, Y, colin_tlrc[:,:,50])
```

We are looking at a single slice in Z.

X and Y are meshgrids providing the x and y coordinates to ax.contour .


But we need to fix the aspect ratio.  We want the pixels to be square.
```
def draw_slice(slice_num):
    fig, ax = plt.subplots()
    contours = ax.contour(X, Y, colin_tlrc[:,:,slice_num])
    ax.set_title(f'slice {slice_num}')
    # set the aspect ratio
    ratio = colin_tlrc.shape[1]/colin_tlrc.shape[0]
    x_left, x_right = ax.get_xlim()
    y_low, y_high = ax.get_ylim()
    ax.set_aspect(abs((x_right - x_left)/(y_low - y_high))*ratio)
draw_slice(50)
```

And we wrapped it in a function for convenience.



There is a notebook that does this, _coordinates_in_colin27.ipynb_ .  Let's use it, and talk
about the coordinate systems of the graphs it produces.